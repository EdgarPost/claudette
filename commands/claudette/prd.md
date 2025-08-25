---
description: Create Product Requirements Document
# allowed-tools:
model: opus
---

First read @~/.claude/claudette/commands-subagents-guide.md and follow the rules and guide.

# Goal

Your goal is to create a Project Requirements Document (PRD) based on a template file.

# Rules

- The PRD is always a feature for this product or project.
- Focus on high-level requirements. Technical design (Spec) and implementation details (Impl) will be created by other commands.

# Process

Follow these steps. Do not skip any.

1. Ask the user to describe the new feature for which to create a PRD
2. For every thing missing required for the PRD, ask the user to fill in the blanks

- When you think you have the details for a blank, verify with the user
- After verification, move on to the next blank
- Only once all details for the PRD are complete, continue to the next step

3. Give the user a small summary and ask if something else must be added. Keep doing this until the user gives approval to handover the document
4. Save the complete markdown document to planning/features/backlog/[feature-name]/prd.md

# Next steps

After creating the PRD, present the link and recommend the user to create a SPEC or another PRD.
