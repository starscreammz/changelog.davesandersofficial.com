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

## [1.7.0] - 2026-08-09

### Added

- **Release commit SHA on changelog entries** — `GET /changelog/entries` now carries two optional release-level fields per entry: `releaseCommitSha` (the commit the release tag points at) and a server-derived `releaseCommitUrl` link to it. The URL is omitted for private repos, mirroring how the release link is masked. Both are additive and absent until the changelog producer supplies the value.

## [1.6.0] - 2026-08-08

### Added

- **Added trusted device management to user self-service portal** — You can now review the devices signed in to your account and sign out of, or remove, any of them individually. New-device sign-in alerts now contain the approximate geo-location of the specific sign-in (from your network, never exact location) and provide a link straight to your device list. ([PR #128](https://github.com/StarScreammZ/api.davesandersofficial.com/pull/128))

### Changed

- **Standards-compliant authentication challenge on responses with code 401** — API responses with a 401 (Unauthorized) status code now strictly include a standard WWW-Authenticate challenge header (per RFC 7235). Client integrations can now rely on a consistent, standards-based signal that authentication is required.
- **Clearer cookie and privacy information distribution** — Cookie and privacy information data (including data controller, your data-subject rights, and the purpose of each cookie) are now published from a single source. This provides centralized control and full consistency across the whole site. ([PR #127](https://github.com/StarScreammZ/api.davesandersofficial.com/pull/127))

## [1.5.1] - 2026-08-03

### Fixed

- **API keys reach the gateway again** — After a gateway upgrade, new and rotated API keys stopped reaching the gateway's configuration, so changes to them had no effect. Keys sync reliably again, and the result of that sync is now reported by the readiness check rather than passing silently.

### Security

- **Social sign-in endpoints are now rate limited** — The endpoints for OAuth methods, which are used for social sign-in, are now covered by a rate-limit profile and no longer accept unlimited requests. They sit behind the same authentication protection as the rest of the system.
- **Password-reset and verification emails are now rate limited per individual address** — Endpoints that send verification emails are now protected against repeated resends to a single address, with a cooldown period between sends. The whole system is also covered by a global limit on outbound mail. This provides more robust protection against repeated abuse and bots.

## [1.5.0] - 2026-08-01

> ℹ️ **Note:** This release adds new-device sign-in alerts. When your account is signed into from a device you have not used before — including a sign-in through a social account — an email notification is sent to you. No action is required; the change takes effect automatically.

### Added

- **Sign-ins from a new device now send the user an email notification** — When your account is signed into from a device you have not used before, you will now receive an email with the device info and a timestamp. This protects users from being exploited via fake login pages. A device stays trusted for about a year as per our data privacy policy.

### Changed

- **Signing in with a social account now warns about a new device** — Signing in with a social account newly alerts the user about a new sign-in via email. Registering an account that way stays silent and is considered identical to the standard registration flow.
- **Apps can now tell you when a recovery code has been used up** — If a recovery code is accepted but the sign-in cannot then be completed, that code is gone. The response now identifies this case on its own, so apps can tell you to use a different recovery code instead of showing generic guidance that does not apply to recovery codes. This covers both signing in and confirming a password reset.

### Fixed

- **A long browser identifier no longer breaks authentication** — Signing in, signing up and confirming a second factor could fail with a server error when the browser sent an unusually long identifier. Such a request is now rejected properly, with an error message description.
- **The published API schema no longer marks optional fields as required** — Fields the API leaves out of a response were still listed as required in the published schema, so generated clients treated them as always present and strict validators rejected valid responses. They are now correctly optional.

## [1.4.0] - 2026-07-27

### Added

- **Custom roles and permission-based access control** — The API now supports custom roles — each can be named, granted a specific set of permissions, and given its own members. Access to every protected part of the API is now fully driven by a permission engine and a security classifier. Role changes require an MFA confirmation and are written to an audit record. ([PR #100](https://github.com/StarScreammZ/api.davesandersofficial.com/pull/100))

### Changed

- **⚠ BREAKING:** **Tier level is now categorized by ordinals** — Endpoints for access management now emit access role ordinals. Clients consuming the field will require a configuration update. ([PR #100](https://github.com/StarScreammZ/api.davesandersofficial.com/pull/100))

### Security

- **Role changes now take effect immediately** — When a user's role changes, their existing sessions lose the old level of access straight away and the old cache is immediately invalidated at the infrastructure level. ([PR #100](https://github.com/StarScreammZ/api.davesandersofficial.com/pull/100))

## [1.3.1] - 2026-07-25

### Security

- **Administration is now driven by full classification of user roles & permissions** — Every administrative section of the API is now protected by a role classifier and by verification of the user's individual permissions. Permissions are now also enforced on the web application's end. An invalid role ordinal is rejected and the request is refused at the API level.

## [1.3.0] - 2026-07-17

### Added

- **Administrative API configuration** — A new administrative interface to read and edit configuration entries; every change is audited and immediately invalidates the client cache.
- **Scoped collaborator access to password management** — Invited collaborators can now be granted access limited strictly to managing their own project's passwords. Full management access requires per-request approval and is always audited.
- **Contact form policy and validation** — The site's central configuration now drives the contact form and strictly enforces its validation rules.

### Changed

- **Faster site-config revalidation** — The configuration endpoint now returns a strong ETag and honours If-None-Match, so clients refresh from their local cache instead of re-downloading the configuration.

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

[Unreleased]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.7.0...HEAD
[1.7.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.6.0...v1.7.0
[1.6.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.5.1...v1.6.0
[1.5.1]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.5.0...v1.5.1
[1.5.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.4.0...v1.5.0
[1.4.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.3.1...v1.4.0
[1.3.1]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.3.0...v1.3.1
[1.3.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.2.0...v1.3.0
[1.2.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.1.0...v1.2.0
[1.1.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/StarScreammZ/changelog.davesandersofficial.com/releases/tag/v1.0.0
