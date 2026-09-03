# zellij-org/zellij context
> refreshed 2026-09-03 | upstream default: main @ af38660c5884f50bb3726682fb92961326c4268f

## Identity & policies
- upstream: zellij-org/zellij, default branch main, primary language Rust, English-first (yes)
- CLA/DCO: none (no CLA bot, no DCO)
- AI-assisted PR policy: unstated (no ban/disclosure language found in repo CONTRIBUTING/.github; org default `.github` has none)
- signed commits required: no (no branch-protection signature requirement)
- PR template: none (no PULL_REQUEST_TEMPLATE.md in repo or .github) -> pipeline fallback body
- issue-first: CONTRIBUTING asks contributors to check with maintainers before doing LARGE work, but there is no hard "must file issue first" gate for small PRs
- external tracker: github

## Conventions (verified from merged PRs + code)
- branch naming: mixed (`fix/...`, `fix-...`, `comment-typos`, `45-release-notes`, PR-head branch names vary)
- commit style: conventional-ish (`fix:`, `feat:`) and plain imperative
- test command: `cargo xtask test` (needs pkg-config + openssl + protoc); format via `cargo xtask format --check`
- CI: GitHub Actions is comprehensive (build/test on ubuntu+macos matrix + windows, integration-test, test-no-web, assets-check, format-check). Nothing substantive missing.
- Merge evidence: maintainers DO merge small outside PRs, but slowly (e.g. #5562 "fix typos in code comments" merged ~2026-09-02). CONTRIBUTING: maintainers overloaded, accept large roadmap projects, minor fixes "might take a long while" (not banned).

## Maintainer picture
- active maintainers: imsnif (Aram, core) + giyany; external contributors merge regularly (55 external merges/60d). imsnif responds to issues but many "suspected bug" threads get diagnostic comments, not approval.

## Issue-area health
- Most open "suspected bug" issues are NOT triaged to an approved/actionable state; no `accepted`/`approved` labels exist; `good first issue`/`help wanted` labels sit on old feature requests, not bugs.
- #5524 — ctrl+mouse-scroll in fullscreen pane: imsnif says expected resize behaviour; ambiguous, not a clean bug.
- #5374 — built-in `link` plugin panic -> 69k OOB traps -> server SIGSEGV: real but non-deterministic; imsnif asked for consistent repro. Not verifiable this run.
- #5572 — `stdin_handler` panic (slice mid<=len assert): real panic, 0 comments, no maintainer triage.
- #4994 [Confirmed] regression — `zellij --layout <file>` (NEW session) silently ignores non-`.kdl` layouts; bisected to 3a26df6314cf (0.44.0); workaround = rename to `.kdl`. REAL, reproducible, maintainer-engaged. Root fix is Rust in layout loading (zellij-server/zellij-utils), which cannot be built/verified on the loop's build-less runner.
- #5442 (this cycle's scoped candidate) — CLAIMED: open upstream PR #5463 (fzlzjerry, "fix(link): preserve pane cwd when opening detected files", open since 2026-08-10, unmerged).

## Gap ledger (dedupe — READ FIRST, never re-pick)
- 2026-09-03 issue #5442 — dropped. Claimed by open upstream PR #5463 (unmerged); never re-implement here (would duplicate a live third-party fix).
- 2026-09-03 issue #4994 — dropped for THIS run. Confirmed, maintainer-engaged regression, but staging a Rust fix unverifiable on this build-less runner violates the evidence rule (no C toolchain / no system openssl headers / no root to install; any host crate build transitively pulls zellij-utils -> isahc -> curl-sys). Reconsider on a build-capable run.

## Mined gaps
- 2026-09-03 docs/clean-code/CI audit — no genuine, uncontested, verifiable NON-code finding:
  - README/CONTRIBUTING.md/docs commands cross-checked against xtask flags (RELEASE.md `cargo x publish --git-remote/--cargo-registry`; CONTRIBUTING `cargo xtask ci e2e --build/--test`, `cargo x proto`) — all exist and match.
  - zellij.dev links (README + docs) — all 200 (curl verified).
  - CI workflows — build/test/integration/test-no-web/assets/format all present; nothing substantive missing.
  - Upstream already merged a comment-typo PR (#5562) — typo vein is fresh; re-doing it would be a duplicate. CONTRIBUTING disfavors trivial.
- 2026-09-03 build note — local Rust verification is infeasible on this runner (no `cc`/`gcc`/`clang`, no root for gcc/openssl-dev). Any future code pick here needs a build-capable runner.
- 2026-09-03 future candidate — #4994 (confirmed `--layout` non-`.kdl` regression) is the highest-value unclaimed pick when a build-capable run next handles zellij.
