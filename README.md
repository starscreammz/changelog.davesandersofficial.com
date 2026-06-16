<div align="center">

# Dave Sanders Official · Changelog

**Public release history for the Web application and API interface.**

[![Live changelog](https://img.shields.io/badge/Live-changelog-00b8d9?style=flat-square)](https://davesandersofficial.com/changelog)
[![Keep a Changelog](https://img.shields.io/badge/Keep%20a%20Changelog-1.1.0-00b8d9?style=flat-square)](https://keepachangelog.com/en/1.1.0/)
[![Semantic Versioning](https://img.shields.io/badge/SemVer-2.0.0-00b8d9?style=flat-square)](https://semver.org/spec/v2.0.0.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-00b8d9?style=flat-square)](LICENSE)

</div>

---

## Overview

This repository is the **public source of record** for the changelogs of the David Sanders **web application** and **API**. Each app keeps its own release history &mdash; the **web** app at the repository root and the **API** under [`api/`](api) &mdash; and every release is mirrored here in three forms:

| Artifact | Audience | Purpose |
| --- | --- | --- |
| `CHANGELOG.md` | People | Human-readable history, grouped by version. |
| `manifest.json` | Machines | Structured, localized release data. |
| [Releases](../../releases) | Both | A tagged GitHub Release per version &mdash; `vX.Y.Z` (web) and `api-vX.Y.Z` (API). |

The polished, multilingual, browsable view lives on the website &mdash; **[davesandersofficial.com/changelog](https://davesandersofficial.com/changelog)**.

## Apps

| App | Location | Manifest | Release tags |
| --- | --- | --- | --- |
| Web application | repository root | [`manifest.json`](manifest.json) | `vX.Y.Z` |
| API | [`api/`](api) | [`api/manifest.json`](api/manifest.json) | `api-vX.Y.Z` |

## `manifest.json`

A single machine-readable document describing every published release &mdash; the canonical feed the website reconciles against. Each app has its own: [`manifest.json`](manifest.json) for the web app, [`api/manifest.json`](api/manifest.json) for the API.

```json
{
  "appSlug": "web",
  "releases": [
    {
      "version": "0.9.10",
      "releasedAt": "2026-06-06T00:00:00.000Z",
      "commitSha": "0121327",
      "entries": [
        {
          "slug": "changelog-delivery-pipeline",
          "category": "feature",
          "title": { "en": "Changelog delivery pipeline", "cs": "Distribuční kanál changelogu" },
          "body":  { "en": "The release pipeline now publishes each version automatically.", "cs": "Pipeline vydání nyní publikuje každou verzi automaticky." }
        }
      ]
    }
  ]
}
```

| Field | Description |
| --- | --- |
| `appSlug` | Product identifier &mdash; `web` (repository root) or `api` ([`api/`](api)). |
| `releases[]` | Every published release. |
| `releases[].version` | Semantic version, no leading `v`. |
| `releases[].releasedAt` | ISO&#8209;8601 UTC timestamp. |
| `releases[].commitSha` | Short commit SHA the release was cut from (informational). |
| `releases[].entries[]` | The individual changes &mdash; each a `category`, `slug`, and localized `title` / `body`. |

## Release categories

Entries are grouped under the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) headings:

| Category | Heading | Meaning |
| --- | --- | --- |
| `feature` | Added | New features or capabilities |
| `improvement` | Changed | Changes to existing behaviour |
| `breaking` | Changed | &#9888; Backwards-incompatible changes |
| `deprecation` | Deprecated | Still available, scheduled for removal |
| `fix` | Fixed | Bug fixes |
| `security` | Security | Vulnerability fixes and hardening |

## How it's maintained

This repository is **updated automatically** by each application's release pipeline (the web app and the API). On every release it mirrors that app's `CHANGELOG.md` + `manifest.json`, publishes a GitHub Release, and notifies the site.

> [!NOTE]
> The files here are generated. Manual edits to `CHANGELOG.md` or `manifest.json` are overwritten on the next release &mdash; changes are authored upstream in the application repositories.

## License

The contents of this repository &mdash; changelog data and documentation &mdash; are released under the [MIT License](LICENSE).

The **David Sanders** name, the *David Sanders Official* brand, and related assets remain &copy; David Sanders.

---

<div align="center">

&copy; 2026 David Sanders. All rights reserved.

<sub>[davesandersofficial.com](https://davesandersofficial.com) · [Changelog](https://davesandersofficial.com/changelog) · [Status](https://status.davesandersofficial.com)</sub>

</div>
