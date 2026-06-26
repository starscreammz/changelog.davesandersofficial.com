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

## [0.10.0] - 2026-06-26

> ℹ️ **Note:** Self-service password reset arrives + a polish pass across the authentication flow.

### Added

- **Self-service password reset** — You can now request a secure reset link by email, then choose a new password. Also, a new two-factor step for accounts that have 2FA enabled.

### Changed

- **Clearer email resend with a countdown** — Resending a password-reset or account-activation email now confirms it was sent and shows a live countdown before you can request another.
- **Refined and consistent auth screens** — A new consistent layout for the whole authentication flow is now live in production.

## [0.9.14] - 2026-06-19

> ℹ️ **Note:** A big rolling update: friendly "Coming soon" sections, time-display preferences, a redesigned changelog, a clearer status page, a refreshed look, and security hardening.

### Added

- **Friendly pages for sections that aren't live yet** — Pages with status now follow a global site routing convention with its dedicated landing page.
- **Choose how dates and times are shown** — A new setting lets you pick your time zone and switch between 12/24-hour clocks. Automated selection based on browser has been added as well.

### Changed

- **A richer changelog** — Release cards now show contributors with avatars, collapsible summaries, links to the source signature of the specific commit and smoother animations.
- **A refreshed look across the site** — A site-wide visual polish brings a new teal gradient to the navigation bar and other sections. Refined dropdown menus, smoother hover effects, and small layout cleanups throughout.
- **A clearer service-status page** — The status page now shows a per-service icon and real service name, an at-a-glance count of monitored services, an "Online" label on each, and clearer handling of services that are newly added and have no data.

### Fixed

- **Assorted display fixes** — Small fixes including a centered status indicator in the footer on iOS, better responsive labels on the status page, and a more accurate Czech translation for the "down" status.
- **Fixed forms that could fail to submit** — Resolved an issue where some form submissions could result in failed action before they were processed.

### Security

- **Stronger sign-in and session security** — Authentication system hardening with automatic session control and strict login policy. Added MFA support and authentication with social networks.

## [0.9.13] - 2026-06-08

> ℹ️ **Note:** Welcome to the new Changelog — every release is now published automatically from GitHub.

### Added

- **Official launch of the Changelog section** — A fully automated release pipeline with a window into GitHub. Entries now carry an author, notes, a publisher, and a general summary.

[Unreleased]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.10.0...HEAD
[0.10.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.9.14...v0.10.0
[0.9.14]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.9.13...v0.9.14
[0.9.13]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/releases/tag/v0.9.13
