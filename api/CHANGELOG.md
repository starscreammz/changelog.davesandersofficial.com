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

## [1.2.0] - 2026-06-25

### Added

- **Public site configuration** — Apps can now fetch feature flags and the announcement banner anonymously and cache the result.
- **Policy and form rules** — Sections with forms can now read the current validation requirements and also verify the form before it's submitted.

### Changed

- **Email confirmation returns the confirmed address** — Verified email address action now returns the same address in the success response, making it easier for the user to check.
- **Consistent lockout signal during password reset** — The two-factor step during password reset now reports a locked account using the same machine-readable code as sign-in.
- **Clearer form errors** — Registration now returns structured, de-duplicated field-level error codes, so validation can pinpoint the exact field.

### Fixed

- **Better name handling** — Names now accept curly/iOS apostrophes, nicknames are canonicalized consistently, and the configured name character set is enforced on registration.
- **Accurate validation error codes in API docs** — The API documentation now describes validation error codes as HTTP 400 instead of 422.

## [1.1.0] - 2026-06-22

### Added

- **Reliable account emails** — Account emails — address confirmation, two-factor codes, and password-reset messages — are now delivered reliably, with automatic handling of bounced or rejected addresses.
- **Self-service password reset** — You can now reset a forgotten password from the sign-in screen through a secure email link. Accounts with two-factor authentication are asked to confirm their second factor during the reset.
- **Two-factor authentication** — Added optional two-factor authentication using an authenticator app, with single-use recovery codes for backup access.

### Changed

- **Clearer authentication responses** — Authentication responses now use a consistent set of machine-readable codes, so apps can present clearer, more specific messages.
- **Build metadata in the API documentation** — The API's OpenAPI document now reports the release version and build date.

### Security

- **Hardened session handling** — Signed-in sessions are more secure: refresh tokens now rotate automatically, with detection of reused tokens.
- **Stronger sign-in protection** — Sign-in and account-recovery flows are now protected against automated abuse, and accounts are temporarily locked after repeated failed sign-in attempts.

## [1.0.0] - 2026-06-16

### Added

- **API added to changelog** — The first stable release of the official API, which is the core for the system infrastructure, is now part of the changelog pipeline.

[Unreleased]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.2.0...HEAD
[1.2.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.1.0...v1.2.0
[1.1.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/releases/tag/v1.0.0
