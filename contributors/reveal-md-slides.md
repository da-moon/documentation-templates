# Reveal-MD Presentation Guidelines

## Rules Table

| Rule ID | Rule Summary                                                           |
| ------- | ---------------------------------------------------------------------- |
| R1      | Use vertical slides for related content within same topic              |
| R2      | Use horizontal slides for top-level topic transitions                 |
| R3      | Include comprehensive speaker notes for each slide                    |
| R4      | Every slide must have a clear header                                  |
| R5      | Maximum 3 bullet points per slide for readability                     |
| R6      | Use bullet points instead of raw paragraphs                           |
| R7      | Provide concrete examples in dedicated vertical slides                |
| R8      | Include diagrams in separate vertical slides                          |
| R9      | Start with problem statement and context slides                       |
| R10     | Clearly state problem, approach, and alternatives                     |
| R11     | Add pause slides for Q&A at logical breakpoints                       |
| R12     | Consider diverse audience backgrounds                                 |
| R13     | Structure for 30-minute presentations                                 |
| R14     | Use markdown syntax for reveal-md compatibility                       |
| R15     | Include visual hierarchy with proper formatting                       |

---

## R1: Use vertical slides for related content within same topic

```markdown
# ❌ BAD - All slides horizontal
---
## Database Design
---
## Schema Overview
---
## Indexing Strategy

# ✅ GOOD - Vertical grouping for related content
---
## Database Design
---
## Database Design
### Schema Overview
---
## Database Design
### Indexing Strategy
```

## R2: Use horizontal slides for top-level topic transitions

```markdown
# ❌ BAD - No clear topic separation
---
## User Authentication
---
## Password Hashing
---
## Payment Processing

# ✅ GOOD - Horizontal for major topics
---
## Authentication Module
---
## Authentication Module
### Implementation Details
---
<!-- Horizontal transition to new topic -->
## Payment Processing
---
## Payment Processing
### Security Considerations
```

## R3: Include comprehensive speaker notes for each slide

```markdown
# ❌ BAD - No speaker notes
---
## Performance Metrics
- Response time: 200ms
- Throughput: 1000 req/s

# ✅ GOOD - Detailed speaker notes
---
## Performance Metrics
- Response time: 200ms
- Throughput: 1000 req/s

Note:
Explain that these metrics were achieved after optimization.
Mention the baseline was 800ms response time.
Highlight that this meets our SLA requirements.
Reference the load testing methodology used.
```

## R4: Every slide must have a clear header

```markdown
# ❌ BAD - Missing headers
---
- Point about architecture
- Another point
- Final point

# ✅ GOOD - Clear headers on all slides
---
## System Architecture Overview
- Microservices design
- Event-driven communication
- Container orchestration
```

## R5: Maximum 3 bullet points per slide for readability

```markdown
# ❌ BAD - Too many points
---
## Implementation Challenges
- Database scaling issues
- Legacy system integration
- Performance bottlenecks
- Security vulnerabilities
- Technical debt
- Resource constraints

# ✅ GOOD - Split across slides
---
## Implementation Challenges (1/2)
- Database scaling issues
- Legacy system integration
- Performance bottlenecks
---
## Implementation Challenges (2/2)
- Security vulnerabilities
- Technical debt
- Resource constraints
```

## R6: Use bullet points instead of raw paragraphs

```markdown
# ❌ BAD - Dense paragraph
---
## Project Status
The project is currently in phase 2 of development with 
the authentication module complete and the payment 
processing system under active development. We expect 
to complete this phase by Q2.

# ✅ GOOD - Bullet points
---
## Project Status
- Phase 2 of development
- Authentication module: ✅ Complete
- Payment processing: 🔄 In progress
- Expected completion: Q2
```

## R7: Provide concrete examples in dedicated vertical slides

```markdown
# ❌ BAD - Abstract concepts only
---
## API Design Patterns
- RESTful endpoints
- Consistent naming

# ✅ GOOD - With example slide
---
## API Design Patterns
- RESTful endpoints
- Consistent naming
---
## API Design Patterns
### Example

```json
GET /api/v1/users/{id}
POST /api/v1/users
PUT /api/v1/users/{id}
DELETE /api/v1/users/{id}
```
```

## R8: Include diagrams in separate vertical slides

```markdown
# ❌ BAD - Text and diagram cramped
---
## Architecture
Here's our architecture with multiple components...
[diagram]

# ✅ GOOD - Dedicated diagram slide
---
## System Architecture
- Distributed microservices
- Message queue integration
- Load balanced
---
## System Architecture
### Diagram

```
┌─────────┐     ┌─────────┐     ┌─────────┐
│   API   │────▶│  Queue  │────▶│ Worker  │
└─────────┘     └─────────┘     └─────────┘
     │                               │
     └───────────┬───────────────────┘
                 ▼
           ┌──────────┐
           │ Database │
           └──────────┘
```
```

## R9: Start with problem statement and context slides

```markdown
# ✅ GOOD - Problem-first structure
---
## Agenda
- Problem Statement
- Current Challenges
- Proposed Solution
- Implementation Plan
---
## The Problem
- 40% increase in failed transactions
- Customer complaints rising
- Revenue impact: $2M/month
---
## Context
- Legacy system limitations
- Recent traffic surge
- Compliance requirements

Note:
Provide background for stakeholders unfamiliar with the technical details.
```

## R10: Clearly state problem, approach, and alternatives

```markdown
# ✅ GOOD - Clear structure
---
## Problem Definition
- Current system can't scale
- Maintenance costs increasing
- Security vulnerabilities identified
---
## Our Approved Approach
- Microservices migration
- Phased rollout
- Zero-downtime deployment
---
## Why Not Alternative X?
- Higher implementation cost
- Longer timeline (18 months vs 6)
- Requires complete retraining

Note:
Be prepared to discuss specific cost comparisons.
Have ROI calculations ready.
```

## R11: Add pause slides for Q&A at logical breakpoints

```markdown
# ✅ GOOD - Strategic Q&A breaks
---
## Technical Overview
[content slides]
---
## Questions?
### Technical Implementation

Note:
Pause here for technical questions before moving to business impact.
Common questions: scaling approach, technology choices, migration strategy.
---
## Business Impact
[content slides]
---
## Questions?
### Business & Timeline

Note:
Address business concerns, ROI, timeline questions.
```

## R12: Consider diverse audience backgrounds

```markdown
# ✅ GOOD - Multi-audience content
---
## For Management
### Business Impact
- ROI: 150% in year 1
- Risk mitigation included
- Competitive advantage
---
## For Engineers
### Technical Implementation
- Kubernetes orchestration
- GraphQL API layer
- PostgreSQL with sharding
---
## For Security
### Security Measures
- Zero-trust architecture
- End-to-end encryption
- SOC2 compliance maintained
```

## R13: Structure for 30-minute presentations

```markdown
# ✅ GOOD - 30-minute structure
---
## Presentation Structure
- Introduction (2 min)
- Problem Statement (5 min)
- Current State Analysis (5 min)
- Proposed Solution (8 min)
- Implementation Plan (5 min)
- Q&A (5 min)

Note:
Keep time markers visible.
Have backup slides for detailed questions.
```

## R14: Use markdown syntax for reveal-md compatibility

```markdown
# ✅ GOOD - Proper reveal-md syntax
---
<!-- .slide: data-background="#1e1e1e" -->
## Title Slide

---
<!-- .slide: data-transition="zoom" -->
## Transition Effect

---
<!-- .slide: class="has-dark-background" -->
## Custom Classes

```markdown
Code example with syntax highlighting
```
```

## R15: Include visual hierarchy with proper formatting

```markdown
# ✅ GOOD - Visual hierarchy
---
# Main Title
## Section Title
### Subsection

**Key Point** in bold

*Emphasis* in italics

`code` inline

> Important quote

1. Ordered item
2. Another item

- Unordered item
- Another item
```

## Best Practices Summary

### Slide Design
- Keep slides clean and focused
- Use consistent formatting throughout
- Include page numbers or progress indicators
- Test presentation on target display

### Content Organization
- Start with executive summary
- Build narrative arc
- End with clear call-to-action
- Prepare appendix slides for deep-dives

### Speaker Preparation
- Practice with timer
- Prepare for common questions
- Have backup data ready
- Test all demonstrations beforehand

### Accessibility
- Use high contrast colors
- Include alt text for images
- Provide handouts if needed
- Speak clearly and pace appropriately