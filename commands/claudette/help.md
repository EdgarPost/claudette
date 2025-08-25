---
description: Help the human
# allowed-tools:
model: sonnet
---

First read @~/.claude/claudette/commands-subagents-guide.md and follow the rules and guide.

# Goal

Your goal is to help the human navigate the optimized Claudette workflow using STATUS.md.
Based on the current project status, recommend which commands to use next.

# Available Commands

## Core Workflow
- `/claudette-feature [name]` - Create new feature with complete PRD+Spec+Implementation plan
- `/claudette-implement` - Systematically execute all tasks with parallel optimization
- `/claudette-status` - Show current project status
- `/claudette-switch [feature-id]` - Switch to different feature

## Setup
- `/claudette-init` - Initialize project structure
- `/claudette-help` - Show this help

# Process

1. **Read STATUS.md** to understand current state
2. **Check if project initialized** - if not, suggest `/claudette-init`
3. **Recommend next logical step**:
   - No active feature → `/claudette-feature`
   - Feature in planning → `/claudette-implement` (systematic execution of all tasks)
   - Feature in progress → `/claudette-status` to see current wave/phase
   - Multiple features → `/claudette-switch`
   - Implementation complete → Review deployment readiness

# Response Format

Show current status and recommend 1-2 next commands with brief explanations.
