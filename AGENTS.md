<!-- BEGIN REPO-PLATFORM MANAGED -->
# AGENTS.md

This file provides guidance to AI coding agents working in this repository. `CLAUDE.md`, `.github/copilot-instructions.md`, and `.github/agents.md` are symlinks to this file, so edit only here.

Everything between the BEGIN and END markers is managed by Vivswan/repo-platform and overwritten by template sync; this repository's own guidance belongs outside the markers (below the END marker at the bottom).

## Project

licenses: Canonical home of versioned software license texts

## Conventions

- PR titles and commit subjects must be Conventional Commits (`feat:`, `fix:`, `feat!:`, `chore:`, ...). PRs are squash-merged, so the PR title becomes the commit subject. CI validates both (the required pr-title check + validate-commit-names).
- CI gates on the required check `all-green`: ci.yml's own `all-green` job needs the `checks` and `ci` caller jobs and fails unless each result is success or skipped, with at least one success (the gate jobs themselves run centrally through repo-platform's fleet-ci.yml; the `pr-title` check is required separately by its own ruleset). This repository's own test/lint jobs belong in `.github/workflows/checks.yml` (repo-owned, called inside the gate); do not edit ci.yml, template sync overwrites it.
- No typographic look-alike characters (curly quotes, em-dashes, invisible unicode). CI enforces this with the check-typography action; use plain ASCII punctuation.

## Managed by repo-platform

- Files whose header says "managed by Vivswan/repo-platform" arrive via sync PRs pushed by that repository. Do not edit them here; change them in Vivswan/repo-platform and let the next sync PR deliver the update.
- Repository settings (description, topics, labels, rulesets, merge policy) are applied from Vivswan/repo-platform: it merges the fleet defaults and this repository's selected-module layers at apply time, then this repository's own `.github/settings.yml` (identity keys and local overrides) over them, and finally a fleet override layer carrying the invariants no repository may weaken (squash-only merging, the branch protection rulesets). A same-name label here replaces the fleet one; a same-name ruleset merges, so you can tighten a fleet ruleset but not strip a rule from it. Do not change settings by hand in the GitHub UI; edit `.github/settings.yml`.
- Repo-owned escape hatches stay local: `.github/workflows/checks.yml`, `.gitleaks.toml`, `.gitignore` outside its BEGIN/END managed region, `.typography-allow.local` (typography exemptions; the managed `.typography-allow` is overwritten by sync), and the repository-specific section below.
- Module selection is this repository's own: edit the `modules` list in `.repo-platform.yml` and the next sync PR applies the change.

## Repository-specific guidance

<!-- Add project-specific instructions below the END marker. They are this
     repository's own and survive template updates. -->
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
