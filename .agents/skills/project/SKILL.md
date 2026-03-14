---
name: project
description: Maintain project-level metadata and skill registry documentation. Use when users add a new root skill, significantly update an existing root skill, or need README synchronization for skill inventory and rationale.
---

# Project Metadata

## Purpose

Use this skill to maintain project-level metadata with `README.md` as the canonical entry:
- Keep the root skill inventory accurate.
- Explain why each maintained root skill exists.
- Enforce README synchronization during skill lifecycle changes.

## Scope And Boundaries

- Scope is limited to project metadata maintenance, primarily root `README.md`.
- Skill inventory scope is fixed to non-hidden root skill directories only.
- Do not include hidden directories (for example `.agents/skills`, `.claude/skills`) in README inventory.
- Do not assume business logic or unstated governance details; ask for clarification when missing.
- Keep this file as routing only; operational details belong in `references/`.

## Core Principles

1. **Single registry source**: root `README.md` is the visible inventory for maintained root skills.
2. **Lifecycle sync**: README must be updated when a root skill is added or materially changed.
3. **Rationale required**: each listed skill includes a concise "why this skill exists" statement.
4. **Deterministic scope**: apply the same inventory filter every time (root + non-hidden only).

## Module Routing

Read modules based on request intent:

1. **Maintain README skill inventory**
   - See [README Skills Maintenance](references/readme-skills-maintenance.md)

## Minimal Output Contract

For any metadata maintenance task, always provide:
- Trigger reason (new skill / major skill change / manual sync).
- Updated inventory entries and rationale text.
- What changed from previous README content.
- Open questions or constraints that still need confirmation.
