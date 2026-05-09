---
name: write-issue
description: Writes a concise issue ticket from the conversation — title, problem, solution, acceptance criteria, out of scope
argument-hint: [filename]
---

Based on our conversation above, write a concise issue ticket for this change.

Structure it as follows:

## Title
One precise line describing the change.

## Problem
What is broken, missing, or painful. Max 3 sentences.

## Proposed Solution
What should concretely change.

## Acceptance Criteria
- [ ] Checkbox list of done conditions.

## Out of Scope
What is explicitly NOT part of this change.

## Technical Notes
Any relevant implementation details from our discussion (omit if none).

If a filename argument is given ($ARGUMENTS), save the document as `docs/$ARGUMENTS.md`. Otherwise save as `docs/issue.md`.
