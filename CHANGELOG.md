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
> A release may open with a **Summary** — a short plain-language overview — and, when relevant, a **Note** (ℹ️ info or ⚠️ warning), both shown above the grouped changes.
>
> **[Unreleased]** lists work merged to `main` that hasn't shipped in a tagged release yet.

## [Unreleased]

_Nothing yet._

## [0.15.0] - 2026-08-25

This release brings a massive visual overhaul. The whole site is being polished, with a consistent look and feel, smooth animations, gentle motion, and a clean "icy" style across buttons, menus, and navigation. The release also adds real conveniences like a full cookie-policy page and scroll preferences that follow you across devices. It's the first major step yet toward the full production release.

### Added

- **Cookie Policy page** — A clear, easy-to-read page showing exactly which cookies we use and why, all grouped by purpose and explained in simple language. Expand or collapse the menu with items using a single click.
- **Know which section you are in as you read** — While you read a page, the footer gently highlights the section you're currently in, so you never lose your place.
- **Scroll and reading indicators** — You can now enable the "scroll back to top" button and the reading-progress indicator bar, which keeps you informed on the scroll and reading status. In case you are signed in, your choices will be remembered and will carry over across all of your signed-in devices.
- **Tidier hashtags on posts and reels** — Posts, photos, and reels now show clean, consistent hashtags, ready to become clickable once tag search arrives.
- **A fresh new look across the site** — We gave the entire site a large visual makeover: buttons, menus, tooltips, and navigation now share one cohesive, modern style with subtle, satisfying motion. It's a big leap toward the finished, production-ready site.

### Changed

- **Clearer buttons and links** — Buttons and links give better feedback now. Keyboard users get a visible highlight, and anything you can't click clearly looks unavailable.
- **Smarter, more consistent behaviour of links** — Every link now behaves the same way and clearly shows where you are on the site. Pages that aren't ready yet appear as "planned" instead of leading to a dead end.
- **Crisper breadcrumbs** — The breadcrumb trail got the new icy styling, and its arrow edges are now smooth and sharp thanks to a rendering adjustment.
- **Various wording touches** — A broad revision of tooltip and label texts across the site for better clarity.

### Fixed

- **Button for scrolling back to top respects your setting** — The "Back to top" button now stays completely hidden when you've turned it off.
- **Disabled links no longer render as clickable** — Links that aren't available now show the correct "not allowed" cursor and clearly render as disabled.

## [0.13.1] - 2026-08-15

### Added

- **CDN-served translations with integrity verification** — Interface translations now load from a content-addressed CDN with deep per-pack integrity checks and regression protection. The fetching falls back to the newest bundled local copy whenever the source can't be reached. This protects translation updates from shipping a partial or stale version.

## [0.12.0] - 2026-08-09

### Added

- **Cookie consent banner and a new preferences panel** — On your first visit you can accept or customize which cookies the site uses. A settings panel offers per-category choices that save automatically, and a floating button in the site footer reopens your preferences at any time.

### Changed

- **Cleaner look for Changelog, Blog, and Gallery** — App and version labels, and the page controls, were tidied for a more consistent, less cluttered look.
- **Cosmetic overhaul for the web UI** — Tooltips, dropdown menus, and filter controls now share one consistent look and coloring across the whole site, including a clearer pointer tip on tooltips.

### Fixed

- **Changelog author shown once per release** — When a release is one person's work spread across several commits, their name now appears a single time in the footer instead of on every entry. Each item still shows its own commit; this behaviour stays unchanged.

## [0.11.1] - 2026-08-01

### Added

- **Choose how you receive your sign-in code** — During two-factor sign-in you can now choose how to verify — your authenticator app, a code sent to your email, or a recovery code. Asking for an email code sends one right away, and if it doesn't arrive you can request another shortly after. If your account has no authenticator app set, the login menu now allows you to choose an alternative method from those at your disposal. The SMS method is still in development.

### Changed

- **Sign-in messages now match the way you received the code** — When a code is rejected, the message now correctly describes the method you used. An authenticator code changes on its own, so the interface tells you to wait for the next one; the code sent via email, however, does not and is one-time only, so you will be advised to request a new one instead.

## [0.10.1] - 2026-07-04

### Added

- **Clearer status page — proxy icon and localized monitor labels** — Added a dedicated proxy glyph and localized monitor-name qualifiers (Primary / Secondary / Tertiary / Reverse) on the status page, so duplicate services like two firewalls read distinctly. ([PR #72](https://github.com/StarScreammZ/davesandersofficial.com/pull/72))

### Fixed

- **Human-verification no longer needs a page refresh** — The Cloudflare Turnstile verification widget now automatically retries when it fails to mint a token (for example after the page has been idle), so forms recover on their own without a manual refresh.

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

[Unreleased]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.15.0...HEAD
[0.15.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.13.1...v0.15.0
[0.13.1]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.12.0...v0.13.1
[0.12.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.11.1...v0.12.0
[0.11.1]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.10.1...v0.11.1
[0.10.1]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.10.0...v0.10.1
[0.10.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.9.14...v0.10.0
[0.9.14]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v0.9.13...v0.9.14
[0.9.13]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/releases/tag/v0.9.13
