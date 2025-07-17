# Tree-sitter Grammar Development Guidelines

## Rules Table

| Rule ID | Rule Summary                                                    |
| ------- | --------------------------------------------------------------- |
| T1      | Use camelCase naming for all grammar rules and symbols          |
| T2      | Define sourceFile as root rule at top of rules object           |
| T3      | Use hidden rules (prefix \_) for internal/intermediate nodes    |
| T4      | Apply field() function to assign semantic names to children     |
| T5      | Refactor complex rules to reduce state count using hidden rules |
| T6      | Store test corpus in test/corpus/ directory with .txt files     |
| T7      | Test format: name separator, code, tree separator, s-expression |
| T8      | Store queries in queries/ directory: highlights.scm, locals.scm |
| T9      | Use specific capture names like @function, @comment, @variable  |
| T10     | Place constants at top of grammar.js for reusable patterns      |
| T11     | Use seq(), choice(), repeat() for clear rule composition        |
| T12     | Export single grammar object using module.exports pattern       |
| T13     | Use prec.left/prec.right for operator associativity             |
| T14     | Use tree-sitter generate --report-states-for-rule optimization  |
| T15     | Implement external scanner in scanner.c for complex lexing      |
| T16     | Include package.json with proper npm scripts and dependencies   |
| T17     | Follow tree-sitter-language repository naming convention        |
| T18     | Use semantic versioning for releases: MAJOR.MINOR.PATCH         |
| T19     | Run tree-sitter test on all changes before committing           |
| T20     | Document grammar limitations and quirks in README.md            |
| T21     | Maintain one-to-one mapping between source files and test files |
| T22     | Use test/sources/ for development, test/corpus/ for validation  |

---

## T1: Use camelCase naming for all grammar rules and symbols

```javascript
// ✅ GOOD - Consistent camelCase naming
module.exports = grammar({
  name: 'lookml',
  rules: {
    sourceFile: $ => repeat($._definition),
    viewDefinition: $ => seq('view', ':', field('name', $.identifier)),
    dimensionDeclaration: $ => seq('dimension', ':', $.block)
  }
});

// ❌ BAD - Inconsistent naming styles
module.exports = grammar({
  rules: {
    source_file: $ => repeat($._definition),     // snake_case
    ViewDefinition: $ => seq(...),              // PascalCase
    'dimension-declaration': $ => seq(...)      // kebab-case
  }
});
```

## T2: Define sourceFile as root rule at top of rules object

```javascript
// ✅ GOOD - Root rule clearly defined first
module.exports = grammar({
  name: 'lookml',
  rules: {
    sourceFile: $ => repeat($._topLevelElement),

    _topLevelElement: $ => choice(
      $.viewDefinition,
      $.exploreDefinition,
      $.modelDefinition
    ),

    viewDefinition: $ => seq('view', ':', field('name', $.identifier))
  }
});

// ❌ BAD - Root rule buried in middle
module.exports = grammar({
  rules: {
    identifier: $ => /[a-zA-Z_][a-zA-Z0-9_]*/,
    sourceFile: $ => repeat($._definition),  // Hard to find
    viewDefinition: $ => seq(...)
  }
});
```

## T3: Use hidden rules (prefix \_) for internal/intermediate nodes

```javascript
// ✅ GOOD - Hidden rules for internal structure
module.exports = grammar({
  rules: {
    sourceFile: ($) => repeat($._definition),

    _definition: ($) =>
      choice(
        // Hidden - not in AST
        $.viewDefinition,
        $.exploreDefinition,
      ),

    viewDefinition: ($) =>
      seq(
        // Public - appears in AST
        "view",
        ":",
        field("name", $.identifier),
        $.block,
      ),
  },
});

// ❌ BAD - All rules public, cluttered AST
module.exports = grammar({
  rules: {
    sourceFile: ($) => repeat($.definition),

    definition: ($) =>
      choice(
        // Public but shouldn't be
        $.viewDefinition,
        $.exploreDefinition,
      ),
  },
});
```

## T4: Apply field() function to assign semantic names to children

```javascript
// ✅ GOOD - Semantic field names for AST navigation
module.exports = grammar({
  rules: {
    viewDefinition: ($) =>
      seq("view", ":", field("name", $.identifier), field("body", $.block)),

    dimensionDeclaration: ($) =>
      seq(
        "dimension",
        ":",
        field("name", $.identifier),
        "{",
        field("properties", repeat($._property)),
        "}",
      ),
  },
});

// ❌ BAD - No field names, harder AST navigation
module.exports = grammar({
  rules: {
    viewDefinition: ($) =>
      seq(
        "view",
        ":",
        $.identifier,
        $.block, // No semantic names
      ),
  },
});
```

## T5: Refactor complex rules to reduce state count using hidden rules

```javascript
// ✅ GOOD - Broken down for manageable state count
module.exports = grammar({
  rules: {
    dimensionDeclaration: ($) =>
      seq(
        "dimension",
        ":",
        field("name", $.identifier),
        field("body", $._dimensionBody),
      ),

    _dimensionBody: ($) => seq("{", repeat($._dimensionProperty), "}"),

    _dimensionProperty: ($) =>
      choice($.typeProperty, $.sqlProperty, $.labelProperty),
  },
});

// ❌ BAD - Complex rule with high state count
module.exports = grammar({
  rules: {
    dimensionDeclaration: ($) =>
      seq(
        "dimension",
        ":",
        $.identifier,
        "{",
        repeat(
          choice(
            seq("type", ":", $.type),
            seq("sql", ":", $.sqlExpression),
            seq("label", ":", $.string),
            // ... many more options inline
          ),
        ),
        "}",
      ),
  },
});
```

## T6: Store test corpus in test/corpus/ directory with .txt files

    // ✅ GOOD - Organized test structure with one-to-one mapping
    test/
    ├── sources/                # Source language files for development
    │   ├── views/
    │   │   ├── basic_view.ext
    │   │   └── complex_view.ext
    │   └── statements/
    │       ├── simple.ext
    │       └── nested.ext
    ├── corpus/                # Corresponding formatted tests
    │   ├── views/
    │   │   ├── basic_view.txt  # Contains basic_view.ext + expected S-expression
    │   │   └── complex_view.txt # Contains complex_view.ext + expected S-expression
    │   └── statements/
    │       ├── simple.txt      # Contains simple.ext + expected S-expression
    │       └── nested.txt      # Contains nested.ext + expected S-expression
    └── highlight/
        └── highlights.scm      # Highlighting tests

    // ❌ BAD - Poor test organization
    test/
    ├── view_test.js           # Wrong format/location
    ├── some_tests.txt         # Non-descriptive names
    └── test1.txt              # Generic names

## T7: Test format: name separator, code, tree separator, s-expression

    ================================================================================
    Basic view definition
    ================================================================================

    view: users {
      dimension: id {
        type: number
      }
    }

    --------------------------------------------------------------------------------

    (sourceFile
      (viewDefinition
        name: (identifier)
        body: (block
          (dimensionDeclaration
            name: (identifier)
            body: (block
              (typeProperty
                value: (type)))))))

## T8: Store queries in queries/ directory: highlights.scm, locals.scm

    // ✅ GOOD - Organized query structure
    queries/
    ├── highlights.scm         # Syntax highlighting
    ├── locals.scm             # Local scope bindings
    ├── injections.scm         # Language injections
    └── tags.scm              # Code navigation

    // ❌ BAD - Poor query organization
    highlight.scm              # Wrong location
    some_highlighting.scm      # Non-standard naming
    queries.scm                # Generic name

## T9: Use specific capture names like @function, @comment, @variable

```scheme
; ✅ GOOD - Specific semantic capture names
(viewDefinition
  name: (identifier) @type)

(dimensionDeclaration
  name: (identifier) @variable)

(comment) @comment

[
  "view"
  "dimension"
  "explore"
] @keyword

; ❌ BAD - Generic or unclear capture names
(identifier) @name          ; Too generic
(viewDefinition) @thing     ; Unclear purpose
(comment) @text             ; Not specific enough
```

## T10: Place constants at top of grammar.js for reusable patterns

```javascript
// ✅ GOOD - Constants defined at top
module.exports = grammar({
  name: "lookml",

  extras: ($) => [
    /\s/, // Whitespace
    $.comment,
  ],

  conflicts: ($) => [[$.propertyName, $.identifier]],

  rules: {
    sourceFile: ($) => repeat($._definition),
    // ... rules using constants
  },
});

// ❌ BAD - Settings scattered throughout
module.exports = grammar({
  name: "lookml",
  rules: {
    sourceFile: ($) => repeat($._definition),
    // rules mixed with configuration
  },
  extras: ($) => [/\s/, $.comment], // Should be at top
});
```

## T11: Use seq(), choice(), repeat() for clear rule composition

```javascript
// ✅ GOOD - Clear composition with helper functions
module.exports = grammar({
  rules: {
    block: ($) => seq("{", repeat($._statement), "}"),

    _statement: ($) => choice($.propertyDeclaration, $.nestedBlock, $.comment),

    propertyDeclaration: ($) =>
      seq(field("key", $.identifier), ":", field("value", $._value)),
  },
});

// ❌ BAD - Unclear structure without helpers
module.exports = grammar({
  rules: {
    block: ($) => ["{", $._statement, "}"], // Unclear array syntax
    _statement: ($) => $.property | $.nested, // Non-standard operators
  },
});
```

## T12: Export single grammar object using module.exports pattern

```javascript
// ✅ GOOD - Standard module export pattern
module.exports = grammar({
  name: 'lookml',

  rules: {
    sourceFile: $ => repeat($._definition),
    // ... grammar rules
  }
});

// ❌ BAD - Non-standard export patterns
const lookmlGrammar = grammar({...});
module.exports = lookmlGrammar;        // Extra variable

export default grammar({...});         // ES6 export syntax

module.exports = {                     // Object wrapper
  grammar: grammar({...})
};
```

## T13: Use prec.left/prec.right for operator associativity

```javascript
// ✅ GOOD - Explicit precedence and associativity
module.exports = grammar({
  rules: {
    expression: ($) =>
      choice($.binaryExpression, $.unaryExpression, $.primaryExpression),

    binaryExpression: ($) =>
      choice(
        prec.left(1, seq($.expression, "+", $.expression)),
        prec.left(1, seq($.expression, "-", $.expression)),
        prec.left(2, seq($.expression, "*", $.expression)),
        prec.left(2, seq($.expression, "/", $.expression)),
      ),
  },
});

// ❌ BAD - No precedence, ambiguous parsing
module.exports = grammar({
  rules: {
    expression: ($) =>
      choice(
        seq($.expression, "+", $.expression), // Ambiguous
        seq($.expression, "*", $.expression), // Conflicts
      ),
  },
});
```

## T14: Use tree-sitter generate --report-states-for-rule optimization

```bash
# ✅ GOOD - Monitor and optimize state count
tree-sitter generate --report-states-for-rule dimensionDeclaration

# Check parser size
wc -l src/parser.c

# Monitor state count during development
grep "STATE_COUNT\|SYMBOL_COUNT" src/parser.c

# ❌ BAD - Ignore performance warnings
tree-sitter generate  # Ignore warnings about large state count
# Never check parser size or complexity
```

## T15: Implement external scanner in scanner.c for complex lexing

```c
// ✅ GOOD - External scanner for context-sensitive tokens
#include <tree_sitter/parser.h>

enum TokenType {
  STRING_CONTENT,
  BLOCK_COMMENT,
  HEREDOC_MARKER
};

bool tree_sitter_lookml_external_scanner_scan(
  void *payload,
  TSLexer *lexer,
  const bool *valid_symbols
) {
  if (valid_symbols[STRING_CONTENT]) {
    return scan_string_content(lexer);
  }

  if (valid_symbols[BLOCK_COMMENT]) {
    return scan_block_comment(lexer);
  }

  return false;
}

// ❌ BAD - Complex lexing in grammar rules
// Trying to handle string interpolation in grammar.js instead of scanner.c
```

## T16: Include package.json with proper npm scripts and dependencies

```json
// ✅ GOOD - Complete package.json configuration
{
  "name": "tree-sitter-lookml",
  "version": "1.0.0",
  "description": "LookML grammar for tree-sitter",
  "main": "bindings/node",
  "keywords": ["parser", "tree-sitter", "lookml"],
  "scripts": {
    "build": "tree-sitter generate && tree-sitter build",
    "test": "tree-sitter test",
    "playground": "tree-sitter build --wasm && tree-sitter playground"
  },
  "dependencies": {
    "node-addon-api": "^7.0.0",
    "node-gyp-build": "^4.6.0"
  },
  "peerDependencies": {
    "tree-sitter": "^0.20.0"
  },
  "tree-sitter": [
    {
      "scope": "source.lookml",
      "file-types": ["lookml", "lkml"]
    }
  ]
}

// ❌ BAD - Minimal or missing package.json
{
  "name": "lookml-parser",
  "version": "1.0.0"
  // Missing scripts, dependencies, tree-sitter config
}
```

## T17: Follow tree-sitter-language repository naming convention

```bash
# ✅ GOOD - Standard repository naming
tree-sitter-javascript
tree-sitter-python
tree-sitter-lookml
tree-sitter-typescript

# ✅ GOOD - Package naming matches
npm: tree-sitter-lookml
PyPI: tree-sitter-lookml
Cargo: tree-sitter-lookml

# ❌ BAD - Non-standard naming
lookml-tree-sitter
ts-lookml
parser-lookml
lookml-grammar
```

## T18: Use semantic versioning for releases: MAJOR.MINOR.PATCH

```bash
# ✅ GOOD - Semantic versioning workflow
# Breaking change to parse tree structure
tree-sitter version 2.0.0
git commit -am "Release 2.0.0"
git tag v2.0.0
git push --tags origin main

# New highlighting features
tree-sitter version 1.1.0

# Bug fixes
tree-sitter version 1.0.1

# ❌ BAD - Inconsistent versioning
git tag release-1
git tag v1.0
git tag 1.0.1-beta
```

## T19: Run tree-sitter test on all changes before committing

```bash
# ✅ GOOD - Complete testing workflow
tree-sitter generate
tree-sitter test
tree-sitter parse examples/*.lkml --quiet

# Test specific areas
tree-sitter test -f "view definitions"
tree-sitter test --update  # Update expectations

# ❌ BAD - Skip testing
git add .
git commit -m "Update grammar"  # No testing
git push
```

## T20: Document grammar limitations and quirks in README.md

```markdown
<!-- ✅ GOOD - Clear limitations documented -->

## Grammar Coverage

This parser covers LookML version 5.x syntax with the following support:

### Supported Features

- View and explore definitions
- Dimension and measure declarations
- Basic SQL expressions
- Comments and documentation

### Known Limitations

- Complex Liquid templating (partial support)
- Advanced derived table syntax
- Legacy parameter syntax (pre-v4.0)

### Reporting Issues

Please include sample LookML code when reporting parsing issues.

<!-- ❌ BAD - No limitations documented -->

# LookML Parser

A tree-sitter parser for LookML.

## Installation

npm install tree-sitter-lookml
```

## T21: Maintain one-to-one mapping between source files and test files

    // ✅ GOOD - One-to-one mapping maintained
    test/sources/views/basic_view.ext      ←→  test/corpus/views/basic_view.txt
    test/sources/statements/simple.ext    ←→  test/corpus/statements/simple.txt

    # Development workflow
    1. Create source file: test/sources/views/my_feature.ext
    2. Test manually: tree-sitter parse test/sources/views/my_feature.ext
    3. Create test file: test/corpus/views/my_feature.txt
    4. Generate expectations: tree-sitter test test/corpus/views/my_feature.txt --update

    // ❌ BAD - No correspondence between source and test files
    test/sources/views/user_view.ext
    test/corpus/misc_tests.txt           # Cannot trace back to source
    test/corpus/view_test_1.txt          # Generic naming

## T22: Use test/sources/ for development, test/corpus/ for validation

    // ✅ GOOD - Clear separation of concerns
    test/sources/                        # Source language files for development
    ├── basic/                          # Simple examples for grammar development
    ├── real_world/                     # Complex real-world examples
    └── edge_cases/                     # Problematic cases to solve

    test/corpus/                        # Formatted tests with expected S-expressions
    ├── basic/                          # Corresponding basic tests
    ├── real_world/                     # Corresponding real-world tests
    └── edge_cases/                     # Corresponding edge case tests

    # Usage
    tree-sitter parse test/sources/basic/simple.ext        # Manual testing
    tree-sitter test test/corpus/basic/simple.txt          # Automated validation

    // ❌ BAD - Mixed purposes in same directory
    test/
    ├── some_source_file.ext            # Source file mixed with tests
    ├── some_test.txt                   # Test mixed with sources
    └── random_file.ext                 # Unclear purpose

---

## Project Structure Pattern

    tree-sitter-lookml/
    ├── grammar.js              # Grammar definition
    ├── src/
    │   ├── parser.c            # Generated parser
    │   ├── tree_sitter/        # Generated headers
    │   └── scanner.c           # External scanner (optional)
    ├── test/
    │   ├── sources/            # Source language files for development
    │   └── corpus/             # Test cases (.txt files) with expected S-expressions
    ├── queries/                # Syntax highlighting
    │   ├── highlights.scm
    │   ├── locals.scm
    │   └── injections.scm
    ├── examples/               # Example LookML files
    ├── package.json            # NPM configuration
    ├── binding.gyp             # Node.js bindings
    ├── README.md               # Documentation
    └── LICENSE                 # License file

## Testing Pattern

```bash
# Generate parser
tree-sitter generate

# Run all tests
tree-sitter test

# Test specific file
tree-sitter test test/corpus/views.txt

# Update test expectations
tree-sitter test --update

# Parse example files
tree-sitter parse examples/sample.lkml

# Performance testing
tree-sitter parse examples/*.lkml --time
```

## Development Workflow Pattern

```bash
# 1. Setup development environment
cargo install tree-sitter-cli
npm install

# 2. Develop grammar iteratively
# Edit grammar.js
tree-sitter generate
tree-sitter test

# 3. Test with real files
tree-sitter parse examples/complex.lkml

# 4. Optimize performance
tree-sitter generate --report-states-for-rule complexRule

# 5. Prepare release
tree-sitter test
tree-sitter version 1.1.0
git commit -am "Release 1.1.0"
git tag v1.1.0
git push --tags origin main
```

## Query Development Pattern

```scheme
; queries/highlights.scm - Syntax highlighting
[
  "view"
  "explore"
  "dimension"
  "measure"
] @keyword

(identifier) @variable

(string_literal) @string

(number_literal) @number

(comment) @comment

; queries/locals.scm - Local scope
(viewDefinition
  name: (identifier) @local.definition)

(dimensionDeclaration
  name: (identifier) @local.definition)
```

## Testing Checklist

- \[ ] All grammar rules follow camelCase naming
- \[ ] Root rule (sourceFile) defined first
- \[ ] Hidden rules used for internal structure
- \[ ] Field names assigned for AST navigation
- \[ ] Test corpus organized in test/corpus/ directory
- \[ ] Queries organized in queries/ directory
- \[ ] External scanner implemented for complex lexing (if needed)
- \[ ] Package.json includes proper scripts and dependencies
- \[ ] Repository follows tree-sitter-language naming
- \[ ] Semantic versioning used for releases
- \[ ] All tests pass before committing
- \[ ] Grammar limitations documented in README
- \[ ] State count monitored and optimized
- \[ ] Performance tested with large files
- \[ ] Syntax highlighting queries implemented
