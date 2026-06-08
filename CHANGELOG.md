# Changelog

All notable changes to **davesandersofficial.com** are documented in this file.

- The format follows [Keep a Changelog 1.1.0](https://keepachangelog.com/en/1.1.0/).
- The project adheres to [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html).
- Entries are generated from changesets in [`changelog.d/`](changelog.d/) and rolled up automatically on each release.

> **Legend** — released changes are grouped under these headings:
>
> | Heading | Meaning |
> | --- | --- |
> | **Added** | New features or capabilities |
> | **Changed** | Changes to existing behaviour (`⚠ BREAKING` = incompatible) |
> | **Deprecated** | Still available, but scheduled for removal |
> | **Removed** | Dropped in this release |
> | **Fixed** | Bug fixes |
> | **Security** | Vulnerability fixes and hardening |
>
> **[Unreleased]** lists work merged to `main` that hasn't shipped in a tagged release yet.

## [Unreleased]

_Nothing yet._

## [0.9.11] - 2026-06-08

### Changed

- **Release links on changelog entries** — Each changelog entry now links directly to its corresponding GitHub Release, with the commit identifier shown as plain reference text.

## [0.9.10] - 2026-06-06

### Added

- **Changelog delivery pipeline** — The release pipeline now publishes each version's changelog to the backend automatically.

## [0.9.9] - 2026-06-02

### Added

- **Repo-side changelog pipeline** — Adds a changeset-based changelog: drop a file in changelog.d/, and releases render CHANGELOG.md and feed the backend digest. ([Spec](https://github.com/StarScreammZ/davesandersofficial.com))

[Unreleased]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.9.11...HEAD
[0.9.11]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.9.10...v0.9.11
[0.9.10]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.9.9...v0.9.10
[0.9.9]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/releases/tag/v0.9.9
