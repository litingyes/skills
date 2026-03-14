---
name: skills-constitution
description: Define governance for creating, updating, and auditing skills. Use whenever a task involves skill design standards, change control, quality evaluation, or generating skill assessment reports.
---

# Skills Constitution

## Purpose

Use this skill as the governance entrypoint for skill lifecycle management:
- Create new skills with consistent structure and trigger quality.
- Update existing skills with compatibility and regression control.
- Audit skills with a weighted rubric and produce standardized reports.

## Scope And Boundaries

- Keep this file minimal: only core principles and routing.
- Put all operational details in `references/` module documents.
- Do not invent business rules when requirements are unclear; clarify first.
- Prioritize practical, maintainable, and non-over-engineered guidance.
- Keep folder conventions aligned with spec: prefer `references/`, `assets/`, and `scripts/`; avoid creating extra top-level folders unless necessary.

## Core Principles

1. **Clarity first**: every rule must be actionable and testable.
2. **Single source of truth**: each topic has one owner document.
3. **Backward safety**: updates must evaluate trigger/behavior regressions.
4. **Evidence-based quality**: audits require reproducible evidence, not opinions.
5. **Iterative improvement**: evaluate, fix, and re-evaluate until pass criteria are met.

## Module Routing

Read the following modules based on user intent:

1. **Create a new skill**
   - See [Create Skill Guide](references/create-skill.md)
2. **Update an existing skill**
   - See [Update Skill Guide](references/update-skill.md)
3. **Audit and evaluate a skill**
   - See [Audit Evaluation Guide](references/audit-evaluation.md)
4. **Generate a formal assessment output**
   - See [Evaluation Report Template](assets/evaluation-report-template.md)

## Quick Decision Flow

1. Identify whether the request is create, update, or audit.
2. Route immediately to the corresponding module.
3. Execute module checklist and collect evidence.
4. If audit is required, score with rubric and output report template.

## Minimal Output Contract

For any lifecycle task, always provide:
- Chosen module and why it applies.
- Completed checklist items.
- Risks or open questions.
- Final status (pass / needs revision) with next actions.


