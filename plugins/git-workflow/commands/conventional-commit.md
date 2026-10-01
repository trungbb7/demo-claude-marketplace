---
description: Generate a standardized Conventional Commit message based on current staged git changes.
---

# Conventional Commit Generator

Inspect current staged git changes (`git diff --staged` or `git status`) and construct a clean commit message following Conventional Commits format:

```text
<type>(<scope>): <short summary in imperative mood>

[optional body describing why and what changed]

[optional footer(s), e.g., BREAKING CHANGE: ..., Fixes #123]
```

## Supported Types:
- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation changes
- `style`: Formatting, missing semi-colons, etc (no code change)
- `refactor`: Refactoring code without changing behavior
- `perf`: Performance improvements
- `test`: Adding or correcting tests
- `chore`: Maintenance, build scripts, configuration changes

## Instructions:
1. Examine staged diffs.
2. Formulate 2-3 suitable commit message options.
3. Offer to run `git commit -m "..."` for the user.
