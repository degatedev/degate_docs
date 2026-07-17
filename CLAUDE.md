# DeGate Docs — Contributing Guide

This repository drives docs.degate.com via GitBook Git Sync. The `multichain-platform` branch is live; work on feature branches and merge via pull request.

## Git workflow

- The repository history is large; clone with `git clone --depth 1 --single-branch --branch <branch>`.
- **Pull before editing**: edits made in the GitBook UI sync back as `GITBOOK-N` commits.
- Merging to `multichain-platform` publishes immediately; treat merges as deliberate releases.

## GitBook conventions

- `SUMMARY.md` is the single table of contents. New pages must be registered there; the homepage is `README.md`.
- File path = URL slug. **Renaming or moving a file changes its URL**; add the old path to `redirects:` in `.gitbook.yaml` in the same change.
- Redirect values must be `.md` file paths (URL-style values without `.md` do not resolve).
- After a sync, GitBook reindexes for roughly 1–2 hours; redirects for just-deleted pages may 404 during that window and then recover. Verify after the window before escalating.
- GitBook-specific syntax: `{% hint style="info" %}...{% endhint %}`, `{% file src="..." %}`, `{% embed url="..." %}`. Images live in `.gitbook/assets/`.
- Image display size: markdown image syntax has no size control; use `<img src="..." width="N">` (confirmed working), and keep source images high-resolution for retina screens.

## Content rules

- Document **shipped functionality only**. Roadmap items, unreleased features, and internal plans do not appear in public docs.
- Product category wording is standardized as **self-custody multichain crypto wallet**; follow the terminology used on the live site and in the app UI (button names as displayed).
- Describe capabilities concretely rather than borrowing regulated-industry category labels (broker/brokerage, exchange, bank) for DeGate itself.
- Every fact must trace to a first-hand source (product, engineering, or verified official pages). Anything unverified is marked `> ⚠️ [NEEDS VERIFICATION: ...]` and must be cleared before merge: `grep -rn "NEEDS VERIFICATION" .` must return empty.
- Numbers and rates carry an "as of [month year]" qualifier. Avoid absolute wording (every/always/only/never) unless factually exact.
- No comparative claims against other products.
- "1:1" wording must always name its exact scope (same-asset cross-chain movement, or an issuer's collateral structure) and is never used between two different assets.
- Write plainly and directly to the reader; avoid marketing tone and em dashes.

## Pre-merge checklist

1. `grep -rn "NEEDS VERIFICATION" .` returns empty
2. New/renamed pages are registered in `SUMMARY.md` and old paths added to `.gitbook.yaml` redirects
3. Product statements reviewed by the content owner
4. After merging, verify the live pages and redirects once the sync completes
