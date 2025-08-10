# Prompt Engineering Guidelines

## Rules Table

| Rule ID | Rule Summary                                                                     |
| ------- | -------------------------------------------------------------------------------- |
| R1      | Use Chain-of-Thought reasoning for complex problem solving                      |
| R2      | Assign specific roles to set expertise context                                  |
| R3      | Include contextual reminders to maintain focus on principles                    |
| R4      | Consider edge cases explicitly in prompts                                       |
| R5      | Use comparison prompting to identify improvements                               |
| R6      | Apply iterative refinement for progressive enhancement                          |
| R7      | Use checklists to ensure comprehensive coverage                                 |
| R8      | Adapt approach based on task complexity                                         |
| R9      | Simulate peer review for quality validation                                     |
| R10     | Start with basic improvements, then add advanced optimizations                  |
| R11     | Assess risks before implementing changes                                        |
| R12     | Consider hypothetical future scenarios                                          |
| R13     | Set specific measurable goals                                                   |
| R14     | Include ethical and inclusive coding considerations                             |
| R15     | Maintain context retention across sessions                                      |
| R16     | Adjust difficulty dynamically based on performance                              |
| R17     | Integrate documentation with code changes                                       |
| R18     | Visualize architecture after significant refactoring                            |
| R19     | Apply deductive reasoning for logical conclusions                               |
| R20     | Use inductive reasoning for pattern recognition                                 |

---

## R1: Use Chain-of-Thought reasoning for complex problem solving

```plaintext
# ❌ BAD - Direct instruction without reasoning
Refactor this code to improve performance.

# ✅ GOOD - Chain-of-Thought approach
Refactor this code step-by-step:
1. First, identify the main performance bottlenecks
2. Explain why each bottleneck impacts performance
3. Apply appropriate optimization techniques
4. Verify each change maintains functionality
5. Document the performance improvements achieved
```

## R2: Assign specific roles to set expertise context

```plaintext
# ❌ BAD - No context or expertise level
Review this code and suggest improvements.

# ✅ GOOD - Role assignment with clear expertise
As a Senior Software Architect with expertise in distributed systems:
- Review this microservice architecture
- Identify scalability bottlenecks
- Suggest improvements following cloud-native patterns
- Consider fault tolerance and resilience
```

## R3: Include contextual reminders to maintain focus on principles

```plaintext
# ❌ BAD - One-time instruction
Apply SOLID principles to this code.

# ✅ GOOD - Contextual reminders throughout
As you refactor this code:
- Remember to prioritize Single Responsibility Principle
- Check periodically that each class has one reason to change
- Ensure Dependency Inversion is maintained
- Validate that interfaces remain segregated
```

## R4: Consider edge cases explicitly in prompts

```plaintext
# ❌ BAD - No edge case consideration
Write a function to parse user input.

# ✅ GOOD - Explicit edge case handling
Write a function to parse user input. Consider these edge cases:
- Empty or null input
- Malformed data formats
- Unicode and special characters
- Maximum length boundaries
- Injection attack patterns
```

## R5: Use comparison prompting to identify improvements

```plaintext
# ❌ BAD - Single version review
Here's my refactored code. Is it good?

# ✅ GOOD - Comparison-based analysis
Compare the original and refactored versions:
1. Identify specific improvements in readability
2. Measure complexity reduction (cyclomatic, cognitive)
3. Highlight performance optimizations
4. Note any potential regressions
5. Suggest further refinements
```

## R6: Apply iterative refinement for progressive enhancement

```plaintext
# ❌ BAD - All-at-once approach
Optimize this entire codebase.

# ✅ GOOD - Iterative refinement
Phase 1: Basic improvements
- Fix obvious code smells
- Standardize naming conventions
- Remove dead code

Phase 2: Structural refactoring
- Extract methods for clarity
- Consolidate duplicate logic
- Improve module boundaries

Phase 3: Advanced optimization
- Implement caching strategies
- Optimize database queries
- Add performance monitoring
```

## R7: Use checklists to ensure comprehensive coverage

```plaintext
# ❌ BAD - Vague requirements
Make this code better.

# ✅ GOOD - Checklist-driven approach
Refactor using this checklist:
□ Each function has single responsibility
□ No functions exceed 20 lines
□ All magic numbers replaced with constants
□ Error handling is comprehensive
□ Logging added at appropriate levels
□ Unit tests cover edge cases
□ Documentation is complete
```

## R8: Adapt approach based on task complexity

```plaintext
# ❌ BAD - One-size-fits-all
Refactor all these files the same way.

# ✅ GOOD - Adaptive complexity handling
Analyze complexity first:
- Simple utilities: Apply basic cleanup
- Core business logic: Detailed refactoring with tests
- Legacy code: Careful incremental changes
- Performance-critical: Profile-guided optimization
Adjust approach based on each component's needs.
```

## R9: Simulate peer review for quality validation

```plaintext
# ❌ BAD - No review process
I've refactored the code. Done.

# ✅ GOOD - Peer review simulation
After refactoring:
1. Review as a colleague would
2. Check for common code review issues:
   - Naming consistency
   - Test coverage
   - Documentation clarity
   - Performance implications
3. Provide constructive feedback
4. Suggest alternative approaches
```

## R10: Start with basic improvements, then add advanced optimizations

```plaintext
# ❌ BAD - Mixed priority changes
Implement all optimizations at once.

# ✅ GOOD - Progressive enhancement
Level 1 - Readability:
- Improve variable names
- Add clarifying comments
- Format consistently

Level 2 - Structure:
- Extract complex logic
- Reduce nesting depth
- Modularize components

Level 3 - Performance:
- Implement caching
- Optimize algorithms
- Add lazy loading
```

## R11: Assess risks before implementing changes

```plaintext
# ❌ BAD - No risk consideration
Refactor this critical payment module.

# ✅ GOOD - Risk assessment approach
Before refactoring the payment module:
1. Identify risks:
   - Breaking existing integrations
   - Introducing security vulnerabilities
   - Performance degradation
2. Mitigation strategies:
   - Comprehensive test suite
   - Feature flags for rollback
   - Gradual rollout plan
3. Proceed only with safeguards in place
```

## R12: Consider hypothetical future scenarios

```plaintext
# ❌ BAD - Present-focused only
Fix the current issues in this code.

# ✅ GOOD - Future-proof thinking
Refactor considering future scenarios:
- 10x increase in user load
- Multi-region deployment needs
- New regulatory requirements
- API versioning requirements
- Third-party service migrations
Design for extensibility and adaptability.
```

## R13: Set specific measurable goals

```plaintext
# ❌ BAD - Vague objectives
Improve the code quality.

# ✅ GOOD - Measurable goals
Refactor with these targets:
- Reduce cyclomatic complexity below 5
- Achieve 80% test coverage
- Decrease response time by 30%
- Reduce memory usage by 25%
- Eliminate all critical linting errors
Track and report progress on each metric.
```

## R14: Include ethical and inclusive coding considerations

```plaintext
# ❌ BAD - No ethical considerations
Build a user profile system.

# ✅ GOOD - Ethical and inclusive approach
Design the user profile system with:
- Gender-neutral field options
- Accessibility compliance (WCAG 2.1)
- Privacy-by-design principles
- Bias-free algorithms
- Inclusive error messages
- Cultural sensitivity in date/time/currency
```

## R15: Maintain context retention across sessions

```plaintext
# ❌ BAD - No context from previous work
Continue working on the project.

# ✅ GOOD - Context retention
Continuing from previous session:
- Recall: We refactored the auth module using JWT
- Pattern: We're using repository pattern throughout
- Standards: TypeScript strict mode is enabled
- Decisions: We chose PostgreSQL over MongoDB
Apply same principles to current task.
```

## R16: Adjust difficulty dynamically based on performance

```plaintext
# ❌ BAD - Fixed difficulty level
Complete all tasks at the same pace.

# ✅ GOOD - Dynamic adjustment
Assess current performance:
- If completing tasks easily:
  * Tackle more complex refactoring
  * Add performance optimizations
  * Implement advanced patterns
- If struggling:
  * Focus on basic improvements
  * Break into smaller tasks
  * Provide more detailed guidance
```

## R17: Integrate documentation with code changes

```plaintext
# ❌ BAD - Code changes without documentation
Refactor these functions.

# ✅ GOOD - Documentation-integrated approach
For each refactoring:
1. Update inline comments explaining why
2. Modify API documentation
3. Update README with new patterns
4. Add migration guide for breaking changes
5. Document performance improvements
6. Include examples of new usage
```

## R18: Visualize architecture after significant refactoring

```plaintext
# ❌ BAD - No architectural overview
The refactoring is complete.

# ✅ GOOD - Architecture visualization
After refactoring, provide:
1. Component diagram showing new structure
2. Sequence diagrams for key workflows
3. Dependency graph highlighting changes
4. Data flow visualization
5. Module boundary definitions

Example ASCII diagram:
┌─────────────┐     ┌──────────────┐
│ Controller  │────▶│   Service    │
└─────────────┘     └──────────────┘
                           │
                           ▼
                    ┌──────────────┐
                    │  Repository  │
                    └──────────────┘
```

## R19: Apply deductive reasoning for logical conclusions

```plaintext
# ❌ BAD - Assumptions without logic
This code probably has issues.

# ✅ GOOD - Deductive reasoning
Given:
- All database queries without indexes are slow
- This query lacks indexes on searched fields
Therefore:
- This query will be slow
- Solution: Add appropriate indexes

Apply this logical approach to identify issues.
```

## R20: Use inductive reasoning for pattern recognition

```plaintext
# ❌ BAD - Missing patterns
Fix each issue individually.

# ✅ GOOD - Inductive pattern recognition
Observed instances:
- Module A: Duplicate validation logic
- Module B: Duplicate validation logic
- Module C: Duplicate validation logic

Pattern identified:
- Validation logic is repeated across modules

General solution:
- Extract shared validation to common module
- Apply DRY principle consistently
```

## Advanced Reasoning Techniques

### Abductive Reasoning
Best explanation from incomplete information:
```plaintext
Observation: Application crashes at midnight
Possible causes: Memory leak, scheduled job, log rotation
Most likely: Scheduled job (fits timing pattern)
Investigation: Check cron jobs and scheduled tasks
```

### Systems Thinking
Understanding interconnected components:
```plaintext
When modifying the cache layer:
- Impact on database load
- Effect on API response times
- Memory usage implications
- Cache invalidation cascades
- Monitoring and alerting changes
```

### Counterfactual Thinking
Exploring alternative scenarios:
```plaintext
What if we had:
- Chosen microservices instead of monolith?
- Used NoSQL instead of relational DB?
- Implemented event-driven architecture?
Analyze trade-offs to validate current approach.
```

### Constraint Satisfaction
Working within limitations:
```plaintext
Constraints:
- Maximum 100ms response time
- 512MB memory limit
- Must support 1000 concurrent users
- Zero downtime deployment required

Solution must satisfy ALL constraints.
```