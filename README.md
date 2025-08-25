# Claudette Enhanced Development Workflow

A comprehensive, interactive development workflow system designed for solo developers who want enterprise-grade feature planning with maximum efficiency and control.

## Overview

Claudette transforms feature development from ad-hoc coding to systematic, user-controlled planning and implementation. Instead of jumping straight into code, you engage in deep collaborative planning that results in comprehensive specifications that need zero clarification.

## Core Philosophy

- **Challenge assumptions** - Don't accept the first solution, explore alternatives
- **User maintains control** - No documentation created without explicit approval
- **Comprehensive before coding** - Engineers receive complete specifications
- **Technology validation** - All tech choices verified against latest best practices
- **Simple workflow** - Complex planning, simple execution

## Workflow Architecture

### File Structure
```
~/.claude/
  commands/claudette/          # All workflow commands
    feature.md                 # Interactive feature creation
    implement.md               # Implementation orchestration  
    status.md                  # Project status overview
    switch.md                  # Feature switching
    help.md                    # Workflow guidance
  agents/                      # Specialized AI agents
    claudette-pm.md            # Planning document management
    claudette-senior-engineer.md # Code implementation
    claudette-lead-architect.md # Technical decisions
    claudette-reviewer.md      # Code quality assurance
  claudette/templates/         # Document templates
    feature.md                 # Comprehensive PRD+Spec template
    tasks.md                   # Detailed implementation tasks
    STATUS.md                  # Project status tracker
    ACTIVITY.md                # Activity logging

project-root/
  planning/
    STATUS.md                  # Active feature pointer
    ACTIVITY.md                # Development activity log
    features/
      0001-feature-name/
        feature.md             # Complete feature specification
        tasks.md               # Implementation roadmap
```

## Command Reference

### Core Workflow Commands

#### `/claudette-feature [name]`
**Purpose**: Create comprehensive features through interactive dialogue

**Process**:
1. **Problem Discovery** - Deep dive into the actual problem
2. **Solution Brainstorming** - Explore 2-3 alternative approaches  
3. **Technical Design** - Detailed architecture with Context7 validation
4. **Implementation Planning** - Specific tasks with time estimates
5. **Final Approval** - User confirms before any files are created

**Output**: 
- Comprehensive `feature.md` (15+ pages) with problem analysis, technical architecture, risk assessment
- Detailed `tasks.md` (25+ pages) with 80+ specific implementation tasks

#### `/claudette-implement`
**Purpose**: Systematically implement all tasks for the active feature

**Process**:
1. Reads STATUS.md to get active feature and all tasks
2. Creates feature branch
3. Executes tasks sequentially in dependency order (Wave 1: Foundation → Wave 2: Services → Wave 3: API → Wave 4: Testing → Wave 5: Deployment)
4. Delegates one task at a time to claudette-senior-engineer
5. Updates progress after each task completion
6. Runs code review after each wave
7. Provides comprehensive progress tracking

#### `/claudette-status`
**Purpose**: Show current project state

**Output**:
```
PROJECT STATUS
Active: User Authentication (3/12 tasks complete)
Phase: Implementation
Current: Implement JWT token validation

TODAY'S ACTIVITY:
- Created feature user-auth with full specifications
- Completed database schema design
- Started authentication service implementation

NEXT ACTIONS:
- /claudette-implement - Continue implementation
- /claudette-switch - Change feature
```

#### `/claudette-switch [feature-id]`
**Purpose**: Switch between features instantly

**Benefit**: No file moving required - just updates STATUS.md pointer

### Specialized AI Agents

#### `claudette-pm` (Haiku - Fast)
- Manages planning documents and project status
- Updates STATUS.md and ACTIVITY.md
- Handles document lifecycle

#### `claudette-senior-engineer` (Opus - Powerful) 
- Implements code based on detailed specifications
- Follows STATUS.md workflow for task management
- Reports progress and issues

#### `claudette-lead-architect` (Opus - Strategic)
- Makes technical architecture decisions
- Validates technology choices with Context7
- Resolves technical uncertainties

#### `claudette-reviewer` (Haiku - Efficient)
- Performs code quality reviews
- Runs security and performance checks
- Provides concise feedback

## Context7 MCP Integration

### Automatic Technology Validation

The workflow automatically validates all technology decisions using Context7 MCP:

**Solution Brainstorming Phase**:
- "What are the latest best practices for [problem domain] in 2025?"
- "Compare [Technology A] vs [Technology B] for [specific use case]"

**Technical Design Phase**:
- "What is the latest stable version of [Framework/Library]?"
- "Are [Technology X] and [Technology Y] compatible in 2025?"
- "What are current security best practices for [specific architecture]?"

**Documentation**: All Context7 findings are recorded in feature specifications with reasoning for choices made.

## Example Workflow Session

### 1. Feature Creation
```bash
Human: /claudette-feature "user authentication"

Claudette: I understand you want user authentication. Let me challenge you:
- What specific problem does this solve for your users?
- Who experiences the pain of not having authentication?
- What's their current workaround?
- Have you considered social login vs email/password?

[Interactive dialogue continues through 5 phases]
[Context7 validates JWT best practices, bcrypt usage, Node.js versions]
[User approves technical design]

Claudette: Perfect! Created comprehensive feature 0003-auth with your 
approved specifications. Ready for /claudette-implement to start development.
```

### 2. Implementation
```bash
Human: /claudette-implement

Claudette: Started implementing User Authentication. Delegated "Design user 
schema" to engineer. Branch: feature/user-auth. Progress: 1/47 tasks.

[Engineer completes task, updates STATUS.md]

Claudette: Completed database schema design. Fixed foreign key constraint 
issue. Updated 2/47 tasks. Next: Implement password hashing service.
```

### 3. Progress Tracking
```bash
Human: /claudette-status

Claudette: 
PROJECT STATUS
Active: User Authentication (15/47 tasks complete) 
Phase: Implementation - API Layer
Current: Implement login endpoint with rate limiting

RECENT PROGRESS:
- Completed all database layer tasks (8/8)
- Finished core authentication services (5/5) 
- Started API endpoint implementation (2/8)

NEXT: /claudette-implement - Continue with login endpoint
```

## Key Benefits

### For Solo Developers

**Before Claudette**:
- Jump into coding without complete understanding
- Discover requirements during implementation
- Frequent scope creep and architecture changes
- Inconsistent documentation and planning

**With Claudette**:
- Comprehensive problem analysis before coding
- Complete technical specifications with user approval
- Clear task breakdown with time estimates
- Consistent, professional documentation

### Performance Improvements

- **10x faster feature switching** via STATUS.md lookup
- **5x fewer file reads** per operation (single status file vs directory scanning)  
- **Context preservation** across sessions via STATUS.md + ACTIVITY.md
- **Sequential task execution** for reliability and simplicity

### Quality Improvements

- **Technology validation** against 2025 best practices
- **Risk assessment** with mitigation strategies
- **Comprehensive testing strategy** built into task breakdown
- **Security considerations** integrated throughout

## Getting Started

### 1. Initialize Project
```bash
/claudette-init
```

### 2. Create Your First Feature
```bash
/claudette-feature "user registration"
```
Follow the interactive dialogue, challenge assumptions, approve technical design.

### 3. Start Implementation  
```bash
/claudette-implement
```
Watch as tasks are completed systematically with progress tracking.

### 4. Monitor Progress
```bash
/claudette-status
```
See exactly where you are and what's next.

## Best Practices

### Feature Creation
- **Be thorough in problem discovery** - The 5-10 questions save hours later
- **Consider multiple solutions** - Don't accept the first approach
- **Challenge the agent** - Ask "what if" questions about scale, edge cases
- **Validate with Context7** - Trust but verify technology recommendations

### Implementation  
- **One feature at a time** - Use STATUS.md to maintain focus
- **Trust the task breakdown** - Follow the systematic approach
- **Review before approving** - Each phase builds on previous decisions

### Quality Assurance
- **Use all agents** - PM for docs, architect for decisions, engineer for code, reviewer for quality
- **Track activities** - ACTIVITY.md provides valuable project history
- **Maintain documentation** - Keep feature.md updated as decisions evolve

## Troubleshooting

### Common Issues

**"Feature creation taking too long"**
- This is intentional - comprehensive planning prevents implementation problems
- Each question in discovery phase saves debugging time later

**"Too many tasks generated"**  
- Tasks are specific for clarity - engineers know exactly what to do
- Time estimates help with realistic planning

**"Context7 recommendations seem outdated"**
- Context7 is consulted for latest information - recommendations are current
- Document why you deviate from Context7 recommendations

### Getting Help

- `/claudette-help` - Show workflow guidance and next steps
- `/claudette-status` - Understand current state
- Review this README for workflow understanding

## Migration from Existing Projects

### From Ad-hoc Development
1. Run `/claudette-init` to set up structure
2. Create `feature.md` for current work using template
3. Break down remaining work into `tasks.md` format
4. Update `STATUS.md` to point to current work

### From Other Planning Systems
1. Convert existing PRDs/specs into `feature.md` format
2. Break down implementation into phase-based `tasks.md`
3. Set up `STATUS.md` tracking for current work

## Advanced Usage

### Multiple Features
Use `/claudette-switch [feature-id]` to work on different features without losing context.

### Custom Templates
Modify templates in `~/.claude/claudette/templates/` to match your project needs.

### Agent Customization
Update agent configurations in `~/.claude/agents/` to match your development style.

## Philosophy: Why This Works

### Systematic Beats Ad-hoc
Most developers jump into coding without comprehensive planning. Claudette forces systematic thinking that prevents costly mistakes.

### User Control Prevents Surprises  
Nothing happens without explicit approval. You maintain complete control over technical decisions.

### Comprehensive Prevents Clarification
Engineers receive complete specifications. No "what did you mean by..." conversations.

### Context Preservation Enables Flow
STATUS.md and ACTIVITY.md preserve context between sessions. Pick up exactly where you left off.

### Technology Validation Reduces Risk
Context7 integration ensures you're using current best practices, not outdated approaches.

---

**Result**: Transform chaotic development into systematic, user-controlled feature delivery with enterprise-grade planning and solo developer efficiency.