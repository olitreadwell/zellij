# zellij-org/zellij context
> refreshed 2026-09-03 | upstream default: main @ af38660c5884f50bb3726682fb92961326c4268f

## Identity & policies
- upstream: zellij-org/zellij, default branch main, primary language Rust, English-first (yes)
- CLA/DCO: none (no CLA bot, no DCO)
- AI-assisted PR policy: unstated (no ban language found)
- signed commits required: no
- PR template: none (no PULL_REQUEST_TEMPLATE.md in repo or .github) -> pipeline fallback body
- external tracker: github

## Conventions (verified from merged PRs)
- branch naming: mixed; `fix/...`, `fix-...`, `comment-typos`, `minor-fixes-for-45-patch`, `45-release-notes`
- commit style: conventional-ish (`fix:`, `feat:`) and plain
- test command: `cargo xtask test` (needs pkg-config + openssl + protoc)
- CI: GitHub Actions; CONTRIBUTING notes maintainers overloaded, minor fixes may take a while

## Maintainer picture
- active maintainers: imsnif (core), plus external contributors merging regularly (55 external merges/60d)

## Issue-area health
- CONTRIBUTING explicitly says minor/trivial fixes may take a long while; not banned, just slow

## Gap ledger (dedupe — READ FIRST, never re-pick)
- (none yet for trivial pass)

## Mined gaps (discovered, not yet attempted)
- (see this run's trivial-fix hunt)
