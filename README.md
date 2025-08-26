# Claudette Development Workflow

A systematic approach to feature development with comprehensive planning and guided implementation.

## What it does

Instead of jumping into code, Claudette helps you:
1. **Plan features thoroughly** with lead architect consultation
2. **Create detailed implementation guides** with code examples  
3. **Implement systematically** following the architect's guidance

## Commands

- `/feature [name]` - Plan a new feature with interactive dialogue and architect consultation
- `/implement` - Execute all tasks for the active feature systematically
- `/status` - Show current project state and progress
- `/switch [id]` - Switch between features

## How it works

### 1. Feature Planning
```bash
/feature "user authentication"
```
- Interactive discovery of the real problem
- Lead architect creates technical proposals
- You discuss and refine until satisfied
- Generates comprehensive specs with implementation details

### 2. Implementation
```bash
/implement  
```
- Executes tasks sequentially using architect's detailed guides
- Each task includes code examples and acceptance criteria
- Progress tracked automatically

### 3. Progress Tracking
```bash
/status
```
Shows active feature, current task, and recent progress.

## Key Benefits

- **No ambiguous tasks** - Every task has detailed implementation guidance from the architect
- **Iterative refinement** - Discuss and adjust proposals until you're satisfied
- **Systematic execution** - Follow proven patterns and code examples
- **Complete specifications** - Engineers get clear, actionable instructions

## File Structure

```
project-root/
  planning/
    STATUS.md              # Points to active feature
    features/
      0001-feature-name/
        feature.md         # Complete specification
        tasks.md           # Detailed implementation guide
```

## Getting Started

1. `/feature "my first feature"` - Create your first feature
2. Follow the interactive planning dialogue  
3. `/implement` - Start systematic implementation
4. `/status` - Check progress anytime

That's it. Comprehensive planning, clear implementation, systematic execution.