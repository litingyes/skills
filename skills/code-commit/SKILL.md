---
name: code-commit
description: Generate a Conventional Commits v1.0.0 compliant git commit message for the current repository, then commit after explicit user confirmation. Use ONLY when the user explicitly invokes this skill or explicitly asks to generate/create a commit message — do NOT auto-trigger for general git questions, coding tasks, or other file edits.
---

# Code Commit

Generate a git commit message following the Conventional Commits 1.0.0 specification for the current repository, then commit after explicit user confirmation.

**This skill is manually invoked only.** Do not use it unless the user explicitly asks for it or explicitly asks to generate a commit message. If the user just wants general git help, answer without using this skill.

## Workflow

1. **Verify the working directory is a git repository**.
   - If not, tell the user and stop.

2. **Inspect the repository state**.
   - Run `git status --porcelain` to see staged, unstaged, and untracked files.
   - Run `git diff --cached --stat` to see the staged change summary.
   - Run `git diff --stat` to see the unstaged change summary.

3. **Handle unstaged/untracked changes**.
   - If there are any unstaged or untracked files, ask the user with a `question` before proceeding:
     - **Stage all changes**: run `git add -A` (or equivalent) and include them in the commit analysis.
     - **Commit only staged changes**: analyze only what is already staged.
     - **Cancel**: stop and do nothing.
   - If the user chooses "Commit only staged changes" and the staging area is empty, tell them there is nothing to commit and stop.

4. **Analyze the changes**.
   - Read the full staged diff (`git diff --cached`). If the diff is very large, first read `git diff --cached --stat`, then read the diffs for the most important files.
   - Read `git log --oneline -5` to infer the project's common scopes and conventions (e.g., whether people use `feat(api):`, `fix(parser):`, etc.).
   - Commit messages must be written in **English** regardless of the user's language.

5. **Generate the commit message** following Conventional Commits 1.0.0.
   - The commit message must follow this structure:
     ```
     <type>[optional scope]: <description>

     [optional body]

     [optional footer(s)]
     ```
   - **Allowed types** (from most common to acceptable): `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`. Prefer `feat` or `fix` when they clearly apply.
   - **Scope**: optional noun in parentheses describing the affected section, e.g., `feat(parser):`. Infer it from the changed files or the project history. Omit if no clear scope exists.
   - **Description**: short summary in the imperative mood, lowercase first letter, no trailing period. Keep it under 72 characters if possible.
   - **Body**: optional. Use it when the change needs explanation of *what* and *why*. Leave one blank line between the description and the body.
   - **Breaking changes**: if the change introduces a breaking API change, append `!` to the type/scope prefix (e.g., `feat(api)!: ...`) and/or add a footer: `BREAKING CHANGE: <description>`.
   - **Footers**: optional. Use git-trailer style, e.g., `Refs: #123`, `Closes: #456`. Footers must be separated from the body by one blank line.

6. **Present the commit message to the user and ask for confirmation**.
   - Show the exact message that will be used.
   - Ask the user with a `question`:
     - **Commit**: execute the commit.
     - **Edit**: let the user provide changes, then regenerate/confirm again.
     - **Cancel**: stop without committing.

7. **Commit** if the user confirms.
   - Use `git commit -m "<subject>" -m "<body>" ...` or another safe method to preserve newlines and footers. Avoid `git commit -m` with a single string containing literal newlines unless you can do so safely.
   - After committing, report the commit hash and short summary.

## Important Notes

- Do not commit without user confirmation.
- Do not auto-stage changes without user approval.
- If the user asks to cancel at any point, stop immediately and do nothing.
- Do not include irrelevant metadata, signatures, or markdown formatting in the final commit message.
- Prefer `feat:` or `fix:` over `chore:` when the change clearly introduces a feature or fixes a bug.
