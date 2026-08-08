# Home Assistant Apps by ibidani

A small [Home Assistant](https://www.home-assistant.io/) **apps** repository
maintained by [ibidani](https://github.com/ibidani). Every app is a containerized,
Cosign-signed, multi-arch image built with the official
[Home Assistant builder](https://github.com/home-assistant/builder) and installed
straight from the Supervisor's store.

![Supports aarch64 Architecture][aarch64-shield] ![Supports amd64 Architecture][amd64-shield]
![CI/CD][ci-shield] ![License: MIT][license-shield]

> **Note:** Home Assistant 2026.2 renamed *add-ons* to **apps**. The repository
> layout, config keys, and CI keep the classic `add-on`/`addon` naming for
> backwards compatibility.

## Getting started

**One-click install** (opens the store dialog on your Home Assistant):

[![Open your Home Assistant instance and show this add-on repository](https://my.home-assistant.io/badges/addon_repository.svg)](https://my.home-assistant.io/redirect/addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fibidani%2Fha-addons)

Or manually:

1. Go to **Settings → Apps → App Store** (on older versions: **Settings → Add-ons → Add-on Store**).
2. Add this repository by URL:
   ```
   https://github.com/ibidani/ha-addons
   ```
3. Find **Obsidian** under Apps and press **Install**.

## Available apps

| App | Description | Architectures |
| --- | --- | --- |
| [Obsidian](obsidian/README.md) | Full desktop [Obsidian](https://obsidian.md/) in your browser; vault lives on the Home Assistant filesystem | `aarch64` `amd64` |

Usage notes, configuration options, and update policy live in each app's own `README.md`.

## Repository layout

```
ha-addons
├── repository.yaml       # store definition (name, URL, maintainer)
├── obsidian/             # one folder per app
│   ├── config.yaml       # app config: slug, version, arch, ports, image…
│   ├── Dockerfile        # pinned multi-arch base + app overlay
│   ├── rootfs/           # s6-overlay init services
│   ├── icon.png / logo.png
│   └── README.md
└── .github/
    ├── workflows/cicd.yaml   # pin base images → build → sign → publish
    ├── renovate.json         # dependency updates
    └── docker-lock.json      # pinned base-image digests
```

Each app is a self-contained folder the Supervisor discovers via its
`config.yaml`. The CI publishes signed multi-arch images to `ghcr.io/ibidani/*`.

## Development

- **Trigger a build:** push to `main`. CI auto-pins base images, builds changed
  apps for each architecture, signs with Cosign, and publishes to GHCR.
- **Release an app update:** bump `version` in the app's `config.yaml`
  and push. Base-image updates arrive automatically via the pinning step.
- **Add a new app:** copy an existing folder, change the slug and metadata in
  `config.yaml`, point `image` at a `ghcr.io/ibidani/*` package, and add it to
  the table above.

The build pipeline is adapted from the [crazyrork/gha-workflows](https://github.com/crazyrokr/gha-workflows)
workflows (auto-lock + multi-arch builder).

## Support

- **Documentation & source:** [github.com/ibidani/ha-addons](https://github.com/ibidani/ha-addons)
- **Bugs & feature requests:** open an [issue](https://github.com/ibidani/ha-addons/issues).

## License

[MIT](LICENSE)

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[ci-shield]: https://img.shields.io/github/actions/workflow/status/ibidani/ha-addons/cicd.yaml?branch=main&label=CI%2FCD&logo=github
[license-shield]: https://img.shields.io/github/license/ibidani/ha-addons.svg