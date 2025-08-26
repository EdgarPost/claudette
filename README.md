# Claudette Development Workflow

A systematic approach to feature development with comprehensive planning, guided implementation, and quality validation.

## What it does

Instead of jumping into code, Claudette helps you:
1. **Plan features thoroughly** with lead architect consultation
2. **Create detailed implementation guides** with code examples  
3. **Implement systematically** with wave-based QA validation
4. **Ensure quality** through progressive testing and validation

## Commands

- `/feature [name]` - Plan a new feature with interactive dialogue and architect consultation
- `/implement` - Execute all tasks for the active feature with QA validation gates
- `/validate` - Validate active feature works correctly
- `/validate [id]` - Validate specific feature by ID  
- `/validate all` - Run full regression suite for all features
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

### 2. Implementation with QA Validation
```bash
/implement  
```
- Executes tasks in waves using architect's detailed guides
- Each task includes code examples and acceptance criteria
- **Wave-level QA validation** before proceeding to next wave
- **Final comprehensive validation** including E2E tests and build verification
- Feedback loops until all validation passes

### 3. Quality Validation
```bash
/validate                    # Validate active feature
/validate 0003-auth         # Validate specific feature  
/validate all               # Full regression suite
```
- Validates features work correctly end-to-end
- Runs all tests (unit, integration, E2E)
- Verifies builds succeed and dev servers start
- Perfect for checking after changes or before deployment

### 4. Progress Tracking
```bash
/status
```
Shows active feature, current task, QA status, and recent progress.

## Key Benefits

- **No ambiguous tasks** - Every task has detailed implementation guidance from the architect
- **Iterative refinement** - Discuss and adjust proposals until you're satisfied
- **Systematic execution** - Follow proven patterns and code examples
- **Quality guaranteed** - Wave-based QA validation ensures working features
- **Stack agnostic** - QA discovers test commands from your project structure
- **Always working** - No broken commits, validate existing features anytime

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
3. `/implement` - Start systematic implementation with QA gates
4. `/validate` - Verify everything works correctly
5. `/status` - Check progress anytime

## Example Workflow

```bash
# Plan a feature
/feature "user authentication"
[Interactive planning with architect proposals and refinement]

# Implement with QA validation
/implement
[Wave 1 complete → QA validation → Wave 2 → QA → Wave 3 → Final QA]

# Validate feature works  
/validate
[✅ All tests pass, feature ready]

# Later, after changes to other features
/validate 0003-auth
[✅ Still working correctly]

# Before deployment
/validate all  
[✅ All features working, safe to deploy]
```

Comprehensive planning, guided implementation, quality validation.