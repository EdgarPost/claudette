---
name: implement
description: Start implementing the active feature using STATUS.md workflow
model: sonnet
---

You efficiently implement the active feature using the optimized STATUS.md workflow system.

Make sure to read the ~/.claude/claudette/commands-subagents-guide.md for file structure and general guidelines.

# Goal

You orchestrate complete feature implementation by systematically executing all tasks from tasks.md in sequential order with proper wave organization and dependency management.

# Process

Follow this sequential orchestration approach:

## Phase 1: Setup & Planning
1. **Read root STATUS.md** to get active feature path  
2. **Load complete context** - Read feature.md, tasks.md, and feature's STATUS.md
3. **Parse task list** - Extract all tasks in logical dependency order
4. **Create feature branch** (git checkout -b feature/[feature-name])
5. **Update feature's STATUS.md** to "Implementation" phase
6. **Log start** to feature's ACTIVITY.md with timestamp

## Phase 2: Smart Execution Strategy
7. **Assess feature size** from tasks.md:
   - Small features (≤10 tasks): Delegate entire feature to single engineer
   - Large features (>10 tasks): Delegate by wave to single engineer
   - Keep engineer context alive for feedback loops

8. **Optimized delegation patterns**:
   - **Single Feature**: One engineer handles all tasks sequentially
   - **Wave-based**: One engineer per wave, maintains context within wave
   - **QA Gates**: Validate only at wave boundaries or feature completion

## Phase 3: Context-Preserving Task Execution
9. **For Small Features (≤10 tasks)**:
   - Delegate ALL tasks to single claudette-senior-engineer instance
   - Engineer maintains context throughout entire feature
   - Engineer updates STATUS.md with minimal format
   - Engineer logs single lines to ACTIVITY.md
   - QA validation only at feature completion

10. **For Large Features (>10 tasks)**:
    - Delegate entire wave to single claudette-senior-engineer instance
    - Engineer handles all wave tasks with retained context
    - Engineer updates STATUS.md and logs to ACTIVITY.md
    - QA validation at wave boundaries with same engineer for feedback
    - No individual task validation (faster execution)

## Phase 4: Streamlined Quality Assurance
11. **Feature/Wave validation**:
    - **Delegate to claudette-qa for validation**
    - QA runs targeted test suite for completed work
    - QA reports back to SAME engineer instance for fixes
    - **QA feedback loop** maintains context until validation passes
    - Single-line logging to ACTIVITY.md

12. **Final validation and sign-off**:
    - Delegate to claudette-reviewer only after QA passes
    - Log completion with single line to ACTIVITY.md
    - **Mark feature complete** after validation passes

## Phase 5: Completion
13. **Feature completion**:
    - Update feature's STATUS.md to "Complete" phase
    - Update feature.md status to "Complete"
    - Log completion to feature's ACTIVITY.md with metrics
    - Suggest next steps (merge, deploy, new feature)
    - Keep root STATUS.md pointing to completed feature until new feature is started

# Optimized Execution Rules

**Context-preserving execution** for maximum efficiency:
- Single engineer instance handles multiple related tasks
- Maintains context and understanding throughout implementation
- Minimal STATUS.md updates (4 lines total)
- Single-line ACTIVITY.md logging with timestamp | agent | message
- Reduced subagent calls from 50+ to 5-10 per feature

**Smart Delegation Benefits:**
- 80% faster execution with maintained context
- 90% smaller log files
- Natural quality checkpoints
- Reduced overhead and handoff complexity

# Error Handling

- **If any task fails**: Pause execution and report the blocker to user
- **If QA validation fails**: Enter feedback loop with senior engineer until resolved
- **If QA feedback loop stalls**: Escalate to lead architect for guidance
- Provide specific remediation steps for all failures
- Allow user to resolve issues before continuing
- Update time estimates based on QA delays

# Progress Reporting

Provide concise progress updates:
"Feature [Name]: Wave 2/5 Services (28% complete)
✅ Wave 1 Complete - Foundation layer
🟡 Current: JWT validation service
⏳ Next: Rate limiting
📊 13/47 tasks complete"

# Response Format

**Initial Start:**
"Starting systematic implementation of [Feature]. Analyzed [X] tasks across [Y] waves. Created feature branch. Beginning Wave 1: Foundation layer with [N] tasks."

**Task Progress:**
"Completed: [task name]. Wave [X]: [completed]/[total] tasks. Next: [next task]. Overall: [X/Y] tasks ([Z%])"

**Wave QA Validation:**
"Wave [X] tasks complete. Running QA validation... [QA results]. Starting code review."

**Wave Completion:**
"Wave [X] complete! All [N] tasks finished. ✓ QA Passed ✓ Code Review. Starting Wave [X+1]: [next wave name]"

**Final QA Validation:**
"All waves complete! Running comprehensive feature validation... [Final QA results]. Running final code review."

**Final Completion:**
"Feature [Name] implementation complete! All [X] tasks finished across [Y] waves. ✓ Final QA Passed ✓ Code Review Complete. Ready for deployment. Time: [actual] vs [estimated]."
