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

3. **Update root STATUS.md**
   - Change active feature path (3-line minimal format)
   - Update timestamp

4. **Log activity**
   - Add to feature's ACTIVITY.md: "- Switched to this feature from [previous]"
   - Add to root ACTIVITY.md if global logging needed

5. **Show new status**
   - Read feature's STATUS.md for detailed progress
   - Display current task and wave progress

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
- Instant switching (just update 3-line root STATUS.md)
- Maintains all feature-specific history
- Context preserved per feature in their own STATUS.md and ACTIVITY.md
- Ultra-fast lookups with minimal root status file