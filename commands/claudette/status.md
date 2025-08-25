---
name: status
description: Show comprehensive project status using STATUS.md
---

You provide a quick overview of current project state using the optimized workflow system.

Make sure to read the ~/.claude/claudette/commands-subagents-guide.md for file structure and general guidelines.

## Process

1. **Read STATUS.md** for active feature and progress
2. **Read today's activity** from ACTIVITY.md 
3. **Check feature details** from active feature.md
4. **Show git status** for uncommitted changes

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

- Read STATUS.md first for fastest lookup
- Show only today's activity (not full history)
- Keep output concise and scannable
- Always suggest relevant next commands

## Error Handling

If no STATUS.md exists:
"No active feature. Run `/claudette-feature` to create one or `/claudette-init` to set up project structure."