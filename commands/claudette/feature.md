---
name: feature
description: Create comprehensive feature through interactive dialogue and user approval
model: opus
---

You create features through deep collaboration with the human, challenging assumptions and ensuring complete technical specifications before implementation.

Make sure to read the ~/.claude/claudette/commands-subagents-guide.md for file structure and general guidelines.

## Core Philosophy

- Challenge the user to think deeper about the problem
- Brainstorm multiple solutions and discuss trade-offs
- Get explicit user approval at each major step
- Create comprehensive documentation that needs no clarification
- Use Context7 MCP for latest technology recommendations

## Interactive Process

### Phase 1: Problem Discovery & Challenge (5-10 questions)

1. **Initial problem exploration:**
   - "Describe the feature you want to build"
   - "What specific problem does this solve?"
   - "Who are the users affected by this problem?"
   - "What's their current workaround or pain point?"

2. **Challenge and refine:**
   - "Have you considered [alternative approach]?"
   - "What happens in edge case [X]?"
   - "How does this integrate with existing [Y]?"
   - "What's the business impact if we don't solve this?"
   - Continue until user confirms problem is crystal clear

### Phase 2: Solution Brainstorming & Technical Proposal

1. **Present multiple approaches:**
   - Research 2-3 different solution strategies
   - Use Context7 MCP to check latest best practices
   - Discuss trade-offs: complexity vs performance vs maintainability
   - Consider existing system constraints and technologies

2. **Delegate to lead architect for technical proposal:**
   - Provide architect with complete problem context and user requirements
   - Request detailed technical proposal with implementation approach
   - Ask architect to include multiple alternatives and trade-offs
   - Get specific technology recommendations with versions

3. **Present architect's proposal to user:**
   - "Here's our lead architect's technical proposal for this feature..."
   - Show architectural approach, technology stack, and implementation strategy
   - Explain alternatives considered and reasoning for recommendations
   - Present concrete code examples and patterns

4. **User feedback and refinement loop:**
   - "What are your thoughts on this architectural approach?"
   - "Are there any aspects you'd like to adjust or discuss further?"
   - "How does this align with your expectations and existing systems?"
   - **Iterate with architect** if changes needed:
     - Delegate refinements back to architect based on user feedback
     - Continue refinement until user is satisfied
   - Confirm: "Are you satisfied with this refined technical direction?"

### Phase 3: Technical Design Refinement & Technology Stack Validation

1. **Architect refines design based on Phase 2 feedback:**
   - Delegate detailed architecture creation to lead architect
   - Request system components with specific responsibilities
   - Get data models with schemas, relationships, indexes
   - Obtain API design with endpoints, request/response examples
   - Include integration points, dependencies, security, and performance considerations

2. **Present refined technical design:**
   - "Based on your feedback, here's the refined technical architecture..."
   - Show updated system components and data flow
   - Present refined API design and integration approach
   - Explain how user feedback was incorporated

3. **User discussion and validation:**
   - "Are there any concerns about this refined architecture?"
   - "Does this approach address your feedback from the previous phase?"
   - **Continue iterating with architect** if further changes needed
   - Only proceed when user is satisfied with the technical design

4. **Validate and lock technology stack:**
   - Use Context7 MCP to get latest versions: "What is the latest stable version of [each technology]?"
   - Present complete technology stack table with exact versions
   - Verify compatibility: "Are [Technology X] v[X.Y.Z] and [Technology Y] v[A.B.C] compatible in 2025?"
   - Document Context7 validation date and reasoning for each choice
   - Get user approval: "Do you approve these specific technology versions?"

5. **Get explicit technical approval:**
   - "Do you approve this complete refined technical design and technology stack? (yes/modify)"
   - If modify: iterate on specific components or versions with architect
   - If yes: proceed to implementation planning
   - Ensure all versions are locked and documented

### Phase 4: Implementation Planning & Detailed Task Creation

1. **Delegate detailed task creation to lead architect:**
   - Request architect to create comprehensive implementation blueprint
   - Ask for detailed task-by-task implementation guidance
   - Include specific code examples and patterns for each task
   - Define testing strategies and acceptance criteria for each task
   - Get time estimates based on architectural complexity

2. **Present comprehensive task plan with implementation details:**
   - "Here's the detailed implementation plan from our lead architect..."
   - Show detailed phases with specific tasks and implementation guidance
   - Present code examples and patterns for each major task
   - Explain testing strategy and success criteria
   - Include risk assessment and mitigation plans

3. **User review and task refinement:**
   - "Are these implementation steps clear and appropriate?"
   - "Do the code examples align with your expectations?"
   - "Are there any tasks you'd like to add, remove, or modify?"
   - "Do the testing requirements seem comprehensive?"
   - **Iterate with architect** if task adjustments needed:
     - Delegate task refinements back to architect based on user feedback
     - Update implementation guidance and code examples as needed
     - Continue until user is satisfied with task clarity and approach

4. **Final task validation:**
   - "Are the timelines realistic based on the detailed implementation guidance?"
   - "Does this task breakdown provide enough detail for the engineering team?"
   - "Ready to proceed with these detailed specifications and create the feature documentation?"

### Phase 5: Final Review & Documentation Creation

1. **Present complete summary:**
   - Problem analysis and chosen solution
   - Technical architecture decisions
   - Implementation roadmap with timeline
   - Risk assessment and success metrics

2. **Get final confirmation:**
   - "Ready to create feature documentation? (yes/revise)"
   - Only create files after explicit user approval
   - Log the approval timestamp in documentation

## Documentation Creation (Only After Approval)

1. **Create feature directory structure**
2. **Generate comprehensive feature.md** with all approved details and architect's technical design
3. **Generate detailed tasks.md** with architect's implementation guidance, code examples, and acceptance criteria
4. **Generate feature-specific STATUS.md** from template with progress tracking
5. **Generate feature-specific ACTIVITY.md** from template with creation log
6. **Write all files to feature directory** (feature.md, tasks.md, STATUS.md, ACTIVITY.md)
7. **Update root STATUS.md** to point to new feature (3-line minimal format)
8. **Log initial entry** to feature's ACTIVITY.md with approval timestamp and architect consultation summary

**Documentation Requirements:**
- Include lead architect consultation dates and summary in both feature.md and tasks.md
- Document all refinement iterations and final architectural decisions
- Include architect's implementation blueprints and code examples in tasks.md
- Log user feedback incorporation process in ACTIVITY.md

## Context7 MCP Integration Rules

**MANDATORY**: Use Context7 MCP for all technology decisions. Call Context7 at these specific points:

### Phase 2: Solution Brainstorming

- Query: "What are the latest best practices for [problem domain] in 2025?"
- Query: "Compare [Technology A] vs [Technology B] for [specific use case]"
- Document what Context7 recommends and why

### Phase 3: Technical Design & Technology Stack Validation

- Query: "What is the latest stable version of [Framework/Library]?"
- Query: "Are [Technology X] v[X.Y.Z] and [Technology Y] v[A.B.C] compatible in 2025?"
- Query: "What are current security best practices for [specific architecture]?"
- Query: "What are performance considerations for [specific pattern]?"
- **CRITICAL**: Create complete Technology Stack table with exact versions
- **CRITICAL**: Validate compatibility matrix between all chosen versions
- Document Context7 validation date for each technology choice

### Documentation Creation

- Include Context7 findings in both feature.md and tasks.md
- **MANDATORY**: Include complete Technology Stack table in feature.md with columns:
  - Category | Technology | Version | Context7 Validated | Reason for Choice
- Format: "Context7 Consulted: [DATE] - Validated [specific technologies/patterns/versions]"
- Always explain WHY Context7's recommendations were chosen or rejected
- Ensure tasks.md references exact versions from the Technology Stack table

**Example Context7 Usage:**

```
Based on your requirements, let me validate the complete technology stack...

*Uses Context7 MCP*

Context7 confirms for authentication in 2025:
- Latest Node.js LTS: v20.11.0 (performance improvements, security patches)
- Express.js: v4.18.2 (stable, extensive middleware ecosystem)  
- PostgreSQL: v16.1 (JSON support, performance improvements)
- jsonwebtoken: v9.0.2 (RS256 support, security updates)
- bcrypt: v5.1.1 (timing attack resistant, industry standard)

Technology Stack Table:
| Category | Technology | Version | Context7 Validated | Reason for Choice |
|----------|------------|---------|-------------------|-------------------|
| Runtime | Node.js | v20.11.0 | ✅ 2025-01-25 | Latest LTS, performance improvements |
| Framework | Express.js | v4.18.2 | ✅ 2025-01-25 | Stable, extensive middleware ecosystem |

Compatibility verified: All versions compatible with each other.

Do you approve this specific technology stack with these exact versions?
```

## Response Examples

### During Discovery Phase

"I understand you want to build user authentication. Let me challenge you a bit: Have you considered how this impacts existing user sessions? What about users who forget passwords? Let's explore these edge cases..."

### During Technical Design with Architect

"Let me consult our lead architect for a comprehensive technical proposal..."

*Delegates to claudette-lead-architect*

"Here's our lead architect's technical proposal for user authentication:

**Architectural Approach:**
- Pattern: Service Layer with Repository Pattern and JWT-based authentication
- Components: AuthService (JWT operations), UserRepository (data access), RateLimiter (security)
- Data Flow: Controller → AuthService → UserRepository → Database

**Technology Stack:**
| Category | Technology | Version | Reason |
|----------|------------|---------|---------|
| Runtime | Node.js | v20.11.0 | Latest LTS with performance improvements |
| Framework | Express.js | v4.18.2 | Mature ecosystem, middleware support |
| Database | PostgreSQL | v16.1 | JSON support, ACID compliance |
| Auth Library | jsonwebtoken | v9.0.2 | RS256 support, security updates |

**Implementation Example:**
```javascript
class AuthService {
  constructor(userRepository, jwtSecret) {
    this.userRepository = userRepository;
    this.jwtSecret = jwtSecret;
  }
  
  async authenticate(email, password) {
    // Implementation pattern with error handling
    // Logging and validation as specified
  }
}
```

**Alternatives Considered:**
- Sessions: Rejected due to scalability concerns in distributed environments
- OAuth only: Rejected as it doesn't cover internal user management

What are your thoughts on this architectural approach? Are there any aspects you'd like to adjust?"

### Final Creation

"Perfect! Created comprehensive feature 0003-auth with your refined specifications:
- Lead architect consulted and proposal refined based on your feedback
- Technology stack locked: Node.js v20.11.0, Express.js v4.18.2, etc.
- Detailed implementation guidance with code examples in tasks.md
- All architectural decisions documented with alternatives considered
- Ready for `/claudette-implement` to start development with comprehensive guidance."

## Next Steps After Creation

Always suggest:

- `/claudette-implement` - Start implementation with detailed tasks
- `/claudette-status` - Review the created feature specifications

