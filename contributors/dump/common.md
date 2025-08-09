## OO Principels

- Encapsulation: Ensure that each class encapsulates its own data and behavior.
  For example, the `VirtualDOM` class should encapsulate the logic for building
  and manipulating the Virtual DOM, while the `LXMLParser` class should
  encapsulate the parsing logic.
- Single Responsibility Principle (SRP): Each class should have a single
  responsibility. For example, the `VirtualDOMBuilder` class should only be
  responsible for building the Virtual DOM, not for parsing XML.
- Dependency Inversion Principle (DIP): High-level modules should not depend on
  low-level modules. Instead, both should depend on abstractions.



--------

@@@@@@@@@@@@@@@@@@@

# Software Development Guidelines

## 1. Write Short Units of Code

### Guideline Explanation

- Small units are easier to understand, reuse, and test.
- When writing new units, don't let them grow above 15 lines of code.
- When a unit grows beyond 15 lines of code, you need to shorten it by
  splitting it into smaller units of no longer than 15 lines of code.
- **Further reading:** Chapter 2 of _Building Maintainable Software_

---

## 2. Write Simple Units of Code

### Guideline Explanation

- Keeping the number of branch points (if, for, while, etc.) low makes units
  easier to modify and test.
- Try to limit the McCabe complexity, that is, the number of branch points plus
  1, in a unit to at most 5.
- You can reduce complexity by extracting sub-branches to separate units of no
  more than 4 branch points.
- **Further reading:** Chapter 3 of _Building Maintainable Software_

---

## 3. Write Code Once

### Guideline Explanation

- When code is copied, bugs need to be fixed in multiple places. This is both
  inefficient and error-prone.
- Avoid duplication by never copy/pasting blocks of code.
- Reduce duplication by extracting shared code, either to a new unit or to a
  superclass.
- **Further reading:** Chapter 4 of _Building Maintainable Software_

---

## 4. Keep Unit Interfaces Small

### Guideline Explanation

- Keeping the number of parameters low makes units easier to understand and
  reuse.
- Limit the number of parameters per unit to at most 2.
- The number of parameters can be reduced by grouping related parameters into
  objects.
- Alternatively, try extracting parts of units that require fewer parameters.
- **Further reading:** Chapter 5 of _Building Maintainable Software_

---

## 5. Separate Concerns in Modules

### Guideline Explanation

- Keep the codebase loosely coupled, as it makes it easier to minimize the
  consequences of changes.
- Identify and extract responsibilities of large modules to separate modules
  and hide implementation details behind interfaces.
- Strive to get modules to have no more than 10 incoming calls.
- **Further reading:** Chapter 6 of _Building Maintainable Software_

---

## 6. Couple Architecture Components Loosely

### Guideline Explanation

- Having loose coupling between top-level components makes it easier to
  maintain components in isolation.
- Do this by minimizing the amount of interface code; that is, code in modules
  that are both called from and call modules of other components (throughput),
  and code in modules that are called from modules of other components
  (incoming).
- You can hide a component's implementation details through various means,
  e.g., using the "abstract factory" design pattern.
- **Further reading:** Chapter 7 of _Building Maintainable Software_

---

## 7. Keep Architecture Components Balanced

### Guideline Explanation

- Balancing the number and relative size of components makes it easier to
  locate code.
- Organize source code in a way that the number of components is between 2 and
  12, and ensure the components are of approximately equal size (keep component
  size uniformity less than 0.71).
- For actionable results, you need to define architecture components, for
  example by configuring a zoom level in the tab on the right of the guideline
  view. A zoom level recognizes as architecture components the folders at a
  particular nesting depth.
- **Further reading:** Chapter 8 of _Building Maintainable Software_

---

## 8. Keep Your Codebase Small

### Guideline Explanation

- Keeping your codebase small improves maintainability, as it's less work to
  make structural changes in a smaller codebase.
- Avoid codebase growth by actively reducing system size.
- Refactor existing code to achieve the same functionality using less volume,
  and prefer libraries and frameworks over "homegrown" implementations of
  standard functionality.
- Strive to keep volume below 20 Person-years.
- **Further reading:** Chapter 9 of _Building Maintainable Software_

---

## 9. Automate Tests

### Guideline Explanation

- Automating tests for your codebase makes development more predictable and
  less risky.
- Add tests for existing code every time you change it.
- For small systems (less than 1,000 lines of code), you should have at least
  some test code and one assertion (currently only checked for Java and C#
  systems).
- For medium systems (less than 10,000 lines of code), the total lines of test
  code should be at least 50% of the total lines of production code, and the
  assert density (percentage of lines of test code containing assertions)
  should be at least 1% (currently only checked for Java and C# systems).
- For large systems (more than 10,000 lines of code), the total lines of test
  code should be at least 50% of the total lines of production code, and the
  assert density should be at least 5% (currently only checked for Java and C#
  systems).
- **Further reading:** Chapter 10 of _Building Maintainable Software_

---

## 10. Write Clean Code

### Guideline Explanation

- Clean code is more maintainable.
- Proactively search and remove code smells.
- Remove useless comments, commented code blocks, and dead code. Refactor
  poorly handled exceptions, magic constants, and poorly named units or
  variables.
- **Further reading:** Chapter 11 of _Building Maintainable Software_



-------
@@@@@@@@@@@@@@@@
