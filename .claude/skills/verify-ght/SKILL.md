---
name: verify-ght
description: Prove a change to this test repo works. The repo has no app, build or tests, only Markdown and config files, so the proof is reading the changed files against what the item asked for. Use before opening a PR, after a merge, or for /verify-ght.
---

# verify-ght

This repo is a test bed for the conductor (ATK-985): no app, no build, no tests. A change is proven by reading it.

1. List what the branch changed: `git diff --stat origin/main...HEAD`, plus `git status --short` for uncommitted files.
2. For each changed file, read it whole and check it against the issue's "Done when" list. A Markdown file must keep a single `#` title on its first line, and every link in it must point at a file in the repo or a full URL.
3. After a merge (`--target main`): `git fetch origin`, then confirm `origin/main` holds the merge commit and each changed file reads as it did on the branch (`git diff <branch> origin/main -- <file>` is empty).

Report each check as VERIFIED, NOT VERIFIED or INCONCLUSIVE, with the command and what it printed.
