---
description: Initialize a new project
# allowed-tools:
model: opus
---

First read @~/.claude/claudette/commands-subagents-guide.md and follow the rules and guide.

# Goal

Your goal is to create a Project Brief based on a template file.

# Process

Follow these steps. Do not skip any.

1. Check if there already is a project brief.

- If already present, ask if user wants to update, otherwise, end this command

1. Read the template file for the project brief
1. Ask the user to describe the project
1. For every thing missing for the project brief, ask the user to fill in the blanks

- Do this one-by-one, not all at once.
- When you think you have the details for a blank, verify with the user
- After verification, move on to the next blank
- Only once all details for the project brief are known, continue to the next step

3. Give the user a small summary and ask if something else must be added. Keep doing this until the user gives permission to create the brief
4. Handover the complete markdown document to the claudette-pm

# Next steps

After your process, recommend the user to create a PRD.
