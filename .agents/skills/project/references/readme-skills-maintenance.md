# README Skills Maintenance

## Goal

Maintain an accurate skill registry in `README.md` and keep it synchronized with the project skill lifecycle.

## Inventory Scope Rule

When maintaining the README skill list, include only:
- Skill directories under `/skills`.
- Directories that contain `SKILL.md`.

Exclude hidden/internal paths, including `.agents/skills` and `.claude/skills`.

## Trigger Conditions

Update `README.md` when any of the following happens:
1. A new skill under `/skills` is added.
2. An existing skill under `/skills` has a major update that changes purpose, scope, routing, or output contract.
3. A user explicitly asks to refresh metadata.

## Change Levels

### Level A - Text polish

- Typo fixes, wording cleanup, or formatting.
- README update is optional unless inventory meaning changes.

### Level B - Major skill update

- Purpose/scope/routing/output contract changes.
- README update is required to keep summary and rationale aligned.

### Level C - New or removed skill under `/skills`

- Skill inventory membership changes.
- README update is mandatory.

## Maintenance Workflow

1. Discover current maintained skills under `/skills` using the scope rule.
2. For each listed skill, extract:
   - One-sentence capability summary.
   - One-sentence "why this skill is needed".
3. Update `README.md` skill list and rationale sections.
4. Add or refresh maintenance rule text:
   - README must be synchronized whenever new skills are added under `/skills` or major skill updates happen.
5. Validate consistency between README and actual skill directories under `/skills`.

## Validation Checklist

- [ ] README skill list matches current skill directories under `/skills`.
- [ ] Each listed skill has both summary and rationale.
- [ ] Hidden/internal skill directories are not listed.
- [ ] Update trigger rules are explicitly documented in README.
- [ ] No broken references to skill paths.

## Required Output

For each maintenance run, report:
- Trigger type and why maintenance was executed.
- Skills added/updated/removed in README.
- Any unresolved ambiguities requiring user confirmation.
