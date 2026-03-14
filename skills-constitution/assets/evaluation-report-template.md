# Evaluation Report Template

Use this template to output a standardized skill audit report.

```markdown
# Skill Audit Report

## 1) Basic Information
- Skill Name:
- Audit Type: (create / update / full)
- Reviewer:
- Date:
- Version/Commit (if available):

## 2) Scope
- In Scope:
- Out of Scope:
- Key Change Context:

## 3) Evidence Summary
- Prompt Set:
  - should-trigger count:
  - should-not-trigger count:
  - edge-case count:
- Artifacts Reviewed:
- Notable Observations:

## 4) Dimension Scores
- Trigger Accuracy (25%): X/5 -> XX.XX
  - Evidence:
  - Notes:
- Instruction Clarity (20%): X/5 -> XX.XX
  - Evidence:
  - Notes:
- Execution Reliability (20%): X/5 -> XX.XX
  - Evidence:
  - Notes:
- Maintainability (15%): X/5 -> XX.XX
  - Evidence:
  - Notes:
- Safety And Constraints (20%): X/5 -> XX.XX
  - Evidence:
  - Notes:

## 5) Total Score And Decision
- Total Score (0-100):
- Decision: (pass / conditional pass / fail)
- Decision Rationale:

## 6) Findings
- [severity] Finding title
  - Impact:
  - Evidence:
  - Recommended Fix:

## 7) Remediation Plan
- Action 1: owner / priority / target date
- Action 2: owner / priority / target date

## 8) Regression Check (For Updates)
- Trigger drift check:
- Routing/link validity:
- Output contract consistency:
- Newly introduced risks:

## 9) Final Conclusion
- Current release recommendation:
- Preconditions (if any):
- Next review checkpoint:
```

## Output Rules

- Always include evidence for each score.
- Do not output only totals without dimension details.
- If conditional/fail, remediation plan is mandatory.
- For update audits, regression section is mandatory.
