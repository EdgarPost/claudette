---
name: status
description: Show comprehensive project status using STATUS.md
---

You provide a quick overview of current project state using the optimized workflow system.

Make sure to read the ~/.claude/claudette/commands-subagents-guide.md for file structure and general guidelines.

## Process

1. **Read root STATUS.md** to get active feature path (3-line lookup)
2. **Read feature's STATUS.md** for detailed progress and current task
3. **Read today's activity** from feature's ACTIVITY.md (feature-specific log)
4. **Check feature details** from active feature.md if needed
5. **Show git status** for uncommitted changes

## Output Format

```
PROJECT STATUS
Active: [feature-name] ([X/Y] tasks complete)
Phase: [Planning|Implementation|Review|Complete]
Current: [current task description]

TODAY'S ACTIVITY:
- [recent activity bullets]

NEXT ACTIONS:
- /claudette-implement - Continue implementation
- /claudette-switch - Change feature  
- /claudette-review - Code review
```

## Performance Rules

- Read root STATUS.md first (3-line file) for fastest feature lookup
- Then read feature's STATUS.md for detailed progress
- Show only today's activity from feature's ACTIVITY.md (not full history)
- Keep output concise and scannable
- Always suggest relevant next commands

## Error Handling

If no root STATUS.md exists:
"No active feature. Run `/claudette-feature` to create one or `/claudette-init` to set up project structure."

If feature's STATUS.md is missing:
"Feature directory found but STATUS.md missing. Feature may need to be recreated or migrated to new format."