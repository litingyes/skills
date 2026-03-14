# Audit Evaluation Guide

## Goal

Provide a standardized, evidence-based audit method to evaluate skill quality and decide pass/fail objectively.

## Audit Inputs

Required inputs:

- Skill files under review.
- Review scope (create/update/full audit).
- Representative prompt set (should-trigger and should-not-trigger).
- Output samples and observed behaviors.

## Audit Dimensions And Weights

Score each dimension from 1 to 5.

1. **Trigger Accuracy (25%)**
   - Description clearly defines WHAT + WHEN.
   - Should-trigger prompts are correctly covered.
   - Should-not-trigger prompts avoid false positives.

2. **Instruction Clarity (20%)**
   - Steps are explicit, ordered, and actionable.
   - Boundaries and decision points are unambiguous.
   - Output contract is clear.

3. **Execution Reliability (20%)**
   - Guidance is deterministic where needed.
   - Critical workflows include checks/validation loops.
   - Edge cases are addressed.

4. **Maintainability (15%)**
   - `SKILL.md` remains core + routing only.
   - Modular files are cohesive and non-duplicative.
   - Naming and terminology are consistent.

5. **Safety And Constraints (20%)**
   - No unsupported assumptions on business logic.
   - Explicit risk controls and clarification points.
   - No unsafe or misleading operational guidance.

## Scoring Formula

For each dimension:

`weightedScore = rawScore(1-5) / 5 * weight`

Total score:

`total = sum(all weightedScore)` (0-100)

## Pass Threshold

- **Pass**: total >= 80 and no dimension < 3.
- **Conditional Pass**: total 70-79 with clear remediation plan.
- **Fail**: total < 70, or any critical dimension score < 3.

Critical dimensions:
- Trigger Accuracy
- Safety And Constraints

## Audit Procedure

1. Define audit scope and collect evidence artifacts.
2. Run prompt-based checks (positive/negative/edge cases).
3. Evaluate each dimension with concrete evidence.
4. Compute weighted score and determine status.
5. Generate formal report using template file.
6. If fail/conditional, create actionable remediation list and re-audit.

## Evidence Requirements

Each scored dimension must include:

- At least one supporting prompt or excerpt.
- Observed behavior/output.
- Why this evidence supports the score.

For any issue found, include:

- Severity (`critical` / `major` / `minor`)
- Impact
- Recommended fix
- Owner and due expectation (if available)

## Prompt Set Design Rule

Use at least:

- 5 should-trigger prompts
- 5 should-not-trigger prompts
- 2 edge-case prompts

Avoid trivial prompts that cannot differentiate quality.

## Re-Audit Loop

If status is conditional/fail:

1. Apply top-priority fixes first.
2. Re-run only affected checks + critical dimensions.
3. Update report with delta from previous run.
4. Close loop only when pass threshold is met.
