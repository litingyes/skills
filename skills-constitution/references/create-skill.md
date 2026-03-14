# Create Skill Guide

## Goal

Provide a complete, repeatable workflow for creating a new skill with strong triggering, clear structure, and verifiable quality.

## Prerequisites

- Confirm target scope: personal skill or project skill.
- Confirm intended user scenarios and non-goals.
- Confirm expected output style and constraints.
- Confirm whether deterministic scripts/resources are needed.

## Step 1 - Clarify Requirements

Collect the minimum set before drafting:

1. What the skill should do (core outcomes).
2. When it should trigger (user phrasing and contexts).
3. What it should produce (output contract).
4. What it must not do (explicit boundaries).
5. How success will be judged (acceptance criteria).

If any of these are missing, ask first. Do not assume business logic.

## Step 2 - Define Skill Identity

### Naming Rules

- Use lowercase letters, numbers, and hyphens only.
- Keep name concise and specific (avoid `helper`, `utils`).
- Keep folder name and frontmatter `name` consistent.

### Description Rules (Critical)

Frontmatter `description` is the primary trigger surface.
It must include both:

- **WHAT**: exact capabilities.
- **WHEN**: concrete trigger contexts and wording patterns.

Write in third person and avoid vague phrasing.

## Step 3 - Design File Structure

Use this baseline:

```text
skill-name/
├── SKILL.md
├── scripts/ (optional)
├── references/ (optional)
│   ├── create-skill.md
│   ├── update-skill.md
│   └── audit-evaluation.md
└── assets/ (optional)
    └── evaluation-report-template.md
```

Design choice:
- Keep `SKILL.md` as core + routing.
- Move guidance modules into `references/`.
- Put reusable output templates into `assets/`.
- Avoid creating extra top-level folders unless strictly necessary.

## Step 4 - Draft SKILL.md (Core + Routing)

`SKILL.md` should include only:

1. Purpose and scope.
2. Boundaries and core principles.
3. Module routing links.
4. Minimal output contract.

Avoid packing detailed procedures into `SKILL.md`.

## Step 5 - Implement Module Documents

Each module doc should provide:

- Goal and applicability.
- Step-by-step workflow.
- Checklist and quality gates.
- Common pitfalls and mitigations.
- Required outputs/evidence.

Prefer one concern per file to keep maintenance simple.

## Step 6 - Validate Before Completion

Run this quality checklist:

- [ ] Name and description follow trigger rules.
- [ ] `SKILL.md` is concise and route-oriented.
- [ ] Detailed logic exists in `references/` files (not duplicated).
- [ ] Terminology is consistent across files.
- [ ] Every checklist item is actionable and testable.
- [ ] No ambiguous or assumption-based business logic.

## Minimal Frontmatter Example

```yaml
---
name: skill-name
description: Clear WHAT + WHEN description with trigger contexts.
---
```

## Common Mistakes

- Overloading `SKILL.md` with all details.
- Description only says what, but not when to trigger.
- Mixing multiple unrelated topics in one reference file.
- Missing acceptance criteria or evidence requirements.
