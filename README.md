# Home Assistant Apps by ibidani

A small [Home Assistant](https://www.home-assistant.io/) **apps** repository
maintained by [ibidani](https://github.com/ibidani). This repository is the
**store** — the app manifests (`config.yaml`), icons, and docs that the
Supervisor reads when you add the repository. The Docker images themselves are
built and published from their source repos.

![Supports aarch64 Architecture][aarch64-shield] ![Supports amd64 Architecture][amd64-shield]
![CI/CD][ci-shield] ![License: MIT][license-shield]

> **Note:** Home Assistant 2026.2 renamed *add-ons* to **apps**. The repository
> layout, config keys, and CI keep the classic `add-on`/`addon` naming for
> backwards compatibility.

## Getting started

**One-click install** (opens the store dialog on your Home Assistant):

[![Your Home Assistant instance and show this add-on repository](https://my.home-assistant.io/badges/addon_repository.svg)](https://my.home-assistant.io/redirect/addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fibidani%2Fha-addons)

Or manually:

1. Go to **Settings → Apps → App Store** (on older versions: **Settings → Add-ons → Add-on Store**).
2. Add this repository by URL:
   ```
   https://github.com/ibidani/ha-addons
   ```
3. Find **Obsidian** under Apps and press **Install**.

## Apps

| App | Description | Architecture | Image |
| --- | --- | --- | --- |
| [Obsidian](obsidian/README.md) | Full desktop [Obsidian](https://obsidian.md/) in your browser; vault lives on the Home Assistant filesystem | `aarch64` `amd64` | `ghcr.io/ibidani/ha-obsidian` |

Usage notes, configuration, and update policy live in the app's own `README.md`.

## Repository layout

```
ha-addons
├── repository.yaml       # store definition (name, URL, maintainer)
└── obsidian/             # one folder per app
    ├── config.yaml       # store manifest: slug, version, arch, image…
    ├── icon.png / logo.png
    └── README.md
```

App folders follow the classic add-on layout so the Supervisor discovers them;
the `image:` field tells it which published image to pull.

## Development

- **Image builds** happen in the source repo, currently
  [ibidani/ha-obsidian](https://github.com/ibidani/ha-obsidian): push to
  `master` there — its CI auto-pins base images, builds both architectures,
  and publishes to `ghcr.io/ibidani/ha-obsidian`.
- **Publish a new app version:** bump `version` in the source repo's
  `obsidian/config.yaml`, then sync the same `version` here so the store
  advertises the new tag.
- **Add a new app:** copy the folder, adjust `config.yaml`, point `image` at
  a published `ghcr.io//ibidani/*` package, and add it to the table above.

The store layout follows [crazyrokr/hassio-addons](https://github.com/crazyrokr/hassio-addons).

## Support

- **Documentation & source:** [github.com/ibidani/ha-addons](https://github.com/ibidani/ha-addons)
- **Bugs & feature requests:** open an [issue](https://github.com/ibidani/ha-addons/issues).

## License

[MIT](LICENSE)

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[ci-shield]: https://img.shields.io/github/actions/workflow/status/ibidani/ha-obsidian/cicd.yaml?branch=master&label=CI%2FCD&logo=github
[license-shield]: https://img.shields.io/github/license/ibidani/ha-addons.svg