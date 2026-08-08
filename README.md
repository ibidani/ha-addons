# Home Assistant App Repository by ibidani

Home Assistant **apps** (formerly *add-ons*) maintained by [ibidani](https://github.com/ibidani),
installed straight from the Supervisor's app store. Built for the
[Home Assistant Docker builder](https://github.com/home-assistant/builder).

![Supports aarch64 Architecture][aarch64-shield] ![Supports amd64 Architecture][amd64-shield]

## Installing

1. In Home Assistant, go to **Settings → Apps → App Store** (or **Settings → Add-ons → Add-on Store** on older versions).
2. Add this repository by URL:
   `https://github.com/ibidani/ha-addons`
3. Install the app of your choice below.

> Home Assistant 2026.2 renamed *add-ons* to **apps**. The repository folders,
> config keys, and CI keep the classic `addon` naming for compatibility.

## Apps

| App | Description | Link |
| --- | --- | --- |
| [Obsidian](obsidian/README.md) | Full desktop Obsidian in your browser, vault on the Home Assistant filesystem | `aarch64` / `amd64` |

Each app folder follows the classic HA add-on layout (`config.yaml`, `Dockerfile`,
`rootfs/`, `icon.png`, `logo.png`) so the [builder](https://github.com/home-assistant/builder)
and supervisor pick it up unchanged. Apps publish multi-arch images to
`ghcr.io/ibidani/*` and are signed with Cosign via CI.

## Development

Trigger a build by pushing to `main` (CI pins base images, then builds, signs,
and publishes the changed apps). See each app's `README.md` for specifics.

## License

[MIT](LICENSE)