---
name: git-standards
description: Best practices for git branch naming, commit history cleanliness, and PR descriptions.
---

# Git Standards & Workflow Guidelines

## Branch Naming Conventions
- Feature: `feature/<short-description>` or `feat/<issue-id>-<description>`
- Bugfix: `fix/<short-description>` or `bugfix/<issue-id>-<description>`
- Release: `release/vX.Y.Z`
- Hotfix: `hotfix/<short-description>`

## Commit Hygiene
- Keep commits atomic: each commit should represent one logical change.
- Never commit secret keys, credentials, or `.env` files.
- Write commit titles in imperative present tense (e.g. "Add feature" not "Added feature").
