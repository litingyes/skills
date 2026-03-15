# Commit and Release

## Goal

Standardize commit quality and release automation:
- Commit messages strictly follow Conventional Commits.
- Version bump uses `bumpp`.
- CHANGELOG generation uses `changelogen` based on commit history.

## When To Use

- Enforcing commit discipline for all contributors.
- Preparing release pipelines for manual or semi-automated shipping.
- Migrating legacy projects to traceable semantic release behavior.

## Workflow

1. Enforce Conventional Commits.
   - Accepted format: `<type>[optional scope]: <description>`.
   - Use a body when the commit needs additional context; keep each point concise and auditable.
   - For large or multi-module commits, the body is required and must be grouped by module (subheading or labeled list).
   - Each module group must include both: what changed, and why/impact (not only file lists).
   - Common types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`.
   - Reject non-conforming commit messages in review/hook checks.
   - Example for large commit body:

```text
feat(frontend): unify auth flows across app shell

auth:
- Replace duplicated token refresh logic with shared utility.
- Prevent inconsistent session expiry handling in edge cases.

routing:
- Add guarded route checks for private pages.
- Reduce unauthorized redirect loops after login.

ui:
- Align login/logout loading states across header and modal.
- Improve user feedback during token refresh retries.
```
2. Configure version bump flow with `bumpp`.
   - Use interactive bump: `npx bumpp`.
   - Optional repo config via `bump.config.ts`:

```typescript
import { defineConfig } from "bumpp";

export default defineConfig({
  // repository-specific options
});
```

3. Generate and maintain changelog with `changelogen`.
   - Preview changelog to console: `npx changelogen@latest`.
   - Bump version and update `CHANGELOG.md`: `npx changelogen@latest --bump`.
   - Full release (bump + changelog + commit + tag): `npx changelogen@latest --release`.
4. Align release command ownership.
   - Decide whether release is owned by `bumpp`, `changelogen`, or a scripted composition.
   - Keep one canonical release command to avoid duplicate tags/commits.

## Quality Gates

- [ ] Recent commits satisfy Conventional Commits format.
- [ ] Large or multi-module commits include a body grouped by module with "change + why/impact".
- [ ] `bumpp` is available and runnable for semantic version bump.
- [ ] `changelogen` is configured/usable to produce `CHANGELOG.md`.
- [ ] Team has one documented canonical release command.
- [ ] Release dry run and rollback strategy are documented.

## Common Pitfalls

- Allowing mixed commit styles that break changelog semantics.
- Writing large commits with subject-only messages and no module-level body context.
- Running both `bumpp` and `changelogen --release` without a clear ownership model.
- Generating changelog from partial or unclean git history.

## Required Output

- Commit policy compliance status.
- Release workflow diagram (or ordered command sequence).
- Gaps, risks, and concrete remediation actions.
