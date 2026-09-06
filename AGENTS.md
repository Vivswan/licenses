<!-- BEGIN REPO-PLATFORM MANAGED -->
# AGENTS.md

Guidance for AI coding agents working in this repository. `CLAUDE.md`, `.github/copilot-instructions.md`, and `.github/agents.md` are symlinks to this file, so edit only here.

Everything between the BEGIN and END markers is managed by Vivswan/repo-platform and overwritten by template sync. This repository's own guidance goes below the END marker.

## Project

licenses: Canonical home of versioned software license texts

## Conventions

- PR titles and commit subjects are Conventional Commits. PRs are squash-merged, so the PR title becomes the commit subject. The `pr-title` check validates the title.
- CI gates on the `all-green` check, required by the managed ruleset. Under `.github/workflows/`, this repository's test and lint jobs go in `checks.yml`, its green-gated work on main in `post-green.yml` (both repo-owned); `ci.yml` is managed.
- Plain ASCII punctuation only: no curly quotes, em-dashes, or invisible unicode. The check-typography gate enforces it.

## Managed by repo-platform

- Files whose header says "managed by Vivswan/repo-platform" arrive via sync PRs from that repository. Do not edit them here; change them there.
- Repository settings are applied from Vivswan/repo-platform's layers plus this repository's own `.github/settings.yml`. Edit that file, never the GitHub UI; the merge rules are in repo-platform's docs/settings.md.
- Repo-owned, never overwritten by sync: `checks.yml`, `post-green.yml`, `.gitleaks.toml`, `.gitignore` outside its managed region, `.typography-allow.local`.
- Module selection is the `modules` list in `.repo-platform.yml`; the next sync PR applies a change. The per-module contracts are in repo-platform's docs/new-repo.md.
- Fleet-wide conventions: repo-platform's docs/fleet-guidelines.md.

## Repository-specific guidance

<!-- Add project-specific instructions below the END marker; they are this repository's own and survive template updates. -->
<!-- END REPO-PLATFORM MANAGED -->

- The markdown files are the product: versioned license texts, one
  directory per license, one file per released version. Published
  version files are immutable; corrections become a new version file.
- Never reflow a license's canonical text: the summary table layout
  and Required-Notice bare URL its versioned texts carry are part of
  the canonical format (markdownlint is tuned for them in
  `.markdownlint-cli2.yaml`).
- Lint locally with `bunx markdownlint-cli2` (globs live in the
  config); wrap new prose at 80 columns.
