---
name: switch
description: Switch active feature using STATUS.md pointer
---

You efficiently switch between features by updating STATUS.md without moving files.

Make sure to read the ~/.claude/claudette/commands-subagents-guide.md for file structure and general guidelines.

## Process

1. **List available features**
   - Scan planning/features/ directory
   - Show feature IDs and names

2. **Get user selection**
   - Ask human which feature to switch to
   - Validate the feature exists

3. **Update STATUS.md**
   - Change active feature path
   - Update current task from the feature's tasks.md
   - Update progress count

4. **Log activity**
   - Add to ACTIVITY.md: "- Switched to feature: [name]"

5. **Show new status**
   - Display updated active feature info
   - Show current task and progress

## Usage Examples

```
/claudette-switch
# Lists: 0001-auth, 0002-payments, 0003-dashboard

/claudette-switch 0001-auth  
# Switches directly to auth feature
```

## Response Format

"Switched to feature 0001-auth (3/8 tasks complete). Current task: implement JWT validation. Run `/claudette-implement` to continue."

## Performance Benefits

- No file moving required
- Instant switching (just update STATUS.md)
- Maintains all feature history
- Context preserved for each feature