# AGENTS.md

This file provides guidance to AI coding agents working in this repository. `CLAUDE.md`, `.github/copilot-instructions.md`, and `.github/agents.md` are symlinks to this file, so edit only here.

Everything above the marker at the bottom of this file is managed by Vivswan/repo-platform and overwritten by template sync; this repository's own guidance belongs below the marker.

## Project

licenses: Canonical home of versioned software license texts

## Conventions

- PR titles and commit subjects must be Conventional Commits (`feat:`, `fix:`, `feat!:`, `chore:`, ...). PRs are squash-merged, so the PR title becomes the commit subject. CI validates both (the ci.yml pr-title job + validate-commit-names).
- CI gates on a single required check named `all-green` in the managed `.github/workflows/ci.yml`. This repository's own test/lint jobs belong in `.github/workflows/checks.yml` (repo-owned, called inside the gate); do not edit ci.yml, template sync overwrites it.
- No typographic look-alike characters (curly quotes, em-dashes, invisible unicode). CI enforces this with the check-typography action; use plain ASCII punctuation.

## Managed by repo-platform

- Files whose header says "managed by Vivswan/repo-platform" arrive via sync PRs pushed by that repository. Do not edit them here; change them in Vivswan/repo-platform and let the next sync PR deliver the update.
- Repository settings (description, topics, labels, rulesets, merge policy) are applied from Vivswan/repo-platform: by the `settings/repos/` file named after this repository over there when one exists, otherwise by this repository's own `.github/settings.yml`. Do not change settings by hand in the GitHub UI; edit the settings file.
- Repo-owned escape hatches stay local: `.github/workflows/checks.yml`, `.gitleaks.toml`, `.gitignore`'s marked LOCAL section, `.typography-allow.local` (typography exemptions; the managed `.typography-allow` is overwritten by sync), and the repository-specific section below.
- Module selection is this repository's own: edit the `modules` list in `.repo-platform.yml` and the next sync PR applies the change.

## Repository-specific guidance

<!-- Add project-specific instructions below. This section survives template
     updates via three-way merge. -->
<!-- repo-platform:local-section -->

- The markdown files are the product: versioned license texts, one
  directory per license, one file per released version. Published
  version files are immutable; corrections become a new version file.
- Never reflow a license's canonical text: the summary table layout
  and Required-Notice bare URL its versioned texts carry are part of
  the canonical format (markdownlint is tuned for them in
  `.markdownlint-cli2.yaml`).
- Lint locally with `bunx markdownlint-cli2` (globs live in the
  config); wrap new prose at 80 columns.
