---
name: write-tech-spec
description: Writes a comprehensive technical specification document from the conversation — overview, design decisions, architecture, implementation plan
argument-hint: [filename]
---

Based on our conversation above, write a comprehensive technical specification document.

Structure it as follows:

## Overview
One-paragraph summary of what we're building and why.

## Goals & Non-Goals
What's in scope and explicitly what's not.

## Design Decisions
For each major decision we discussed: the decision, the alternatives considered, and the rationale.

## Architecture / Data Model
Key components, their responsibilities, and how they interact.

## Implementation Plan
Ordered steps to build this, with dependencies noted.

## Open Questions
Anything that came up but wasn't fully resolved.

If a filename argument is given ($ARGUMENTS), save the document as `docs/$ARGUMENTS.md`. Otherwise print it directly.
