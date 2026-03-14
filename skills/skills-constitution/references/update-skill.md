# Update Skill Guide

## Goal

Update an existing skill safely without breaking trigger behavior, output expectations, or maintainability.

## Update Principles

1. Preserve skill identity unless migration is intentional.
2. Make the smallest effective change first.
3. Use change-level classification to decide verification depth.
4. Compare before/after behavior with evidence.

## Step 1 - Baseline Capture

Before editing, record:

- Current `name` and `description`.
- Existing module structure and routing.
- Known trigger scenarios.
- Current expected outputs.
- Existing issues and user feedback.

This baseline is required for regression checks.

## Step 2 - Classify Change Level

### Level A - Text/Documentation Update

- Wording clarity, typo fixes, formatting.
- Expected risk: low.
- Verification: checklist + spot review.

### Level B - Behavioral Guidance Update

- Workflow steps, decision logic, output templates.
- Expected risk: medium.
- Verification: checklist + prompt-based scenario validation.

### Level C - Structural/Trigger Surface Update

- Frontmatter description changes, routing changes, module split/merge.
- Expected risk: high.
- Verification: full regression pass + audit scoring.

## Step 3 - Perform Controlled Changes

- Keep `name` stable by default.
- Update `description` carefully; reevaluate trigger scope.
- Ensure `SKILL.md` remains core + routing only.
- Put detailed edits into the correct file under `references/`.
- Remove duplication and stale references.

## Step 4 - Regression Checklist

- [ ] Trigger coverage unchanged or intentionally improved.
- [ ] No accidental broad/false trigger wording.
- [ ] Output contract still clear and consistent.
- [ ] Links/routes point to valid reference docs.
- [ ] Terminology consistent across all files.
- [ ] Previous known issues addressed without new ones.

## Step 5 - Validation Depth by Change Level

- **Level A**: document QA + link/path check.
- **Level B**: 3-5 representative prompts (normal + edge cases).
- **Level C**: full audit rubric scoring + formal report output.

## Update Risks And Mitigations

1. **Risk: Trigger drift**
   - Mitigation: compare old/new description with should-trigger and should-not-trigger prompts.
2. **Risk: Routing breaks**
   - Mitigation: validate every linked module path and section intent.
3. **Risk: Hidden behavior change**
   - Mitigation: require evidence snapshots for key scenarios.
4. **Risk: Over-engineering**
   - Mitigation: reject changes that add complexity without measurable quality gain.

## Completion Criteria

An update is complete only when:

- Regression checklist passes.
- Required validation depth is executed.
- Changes are traceable to requirements.
- Open risks are documented with next actions.
