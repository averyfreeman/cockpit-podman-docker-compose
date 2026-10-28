# Cockpit Docker/Podman Compose Plugin

[![CI](https://github.com/averyfreeman/cockpit-podman-docker-compose/actions/workflows/ci.yml/badge.svg)](https://github.com/averyfreeman/cockpit-podman-docker-compose/actions/workflows/ci.yml)
[![Packaging](https://github.com/averyfreeman/cockpit-podman-docker-compose/actions/workflows/pkg-ci.yml/badge.svg)](https://github.com/averyfreeman/cockpit-podman-docker-compose/actions/workflows/pkg-ci.yml)

A maintained fork of [RXTX4816/cockpit-compose](https://github.com/RXTX4816/cockpit-compose), for managing Docker and Podman Compose stacks from [Cockpit](https://cockpit-project.org).

![Screenshot](docs/assets/overview.png)

## Features

| | |
|---|---|
| **Dashboard** | Every stack with live status, CPU and memory; search, filter, four layouts |
| **Stack actions** | Up, Down, Restart, Pause, Pull, Scale, Kill — one stack or many at once, optionally in the background |
| **Create & import** | Start from scratch or a Git URL, or adopt stacks already on disk |
| **Edit** | YAML editor with validation, diff view and snapshots, plus a `.env` editor |
| **Inspect** | Live logs with service filter and search, events, processes, stack info |
| **Shell & run** | Shell into a service or run one-off commands and Compose jobs |
| **Maintain** | Prune per stack or host-wide, backup and restore as `.bak.tar.gz` |
| **Runtimes** | Docker and Podman, rootless and rootful, switchable when both exist |

Each feature is described in the [wiki](docs/wiki/Home.md).

## Requirements

- Cockpit 300+
- Docker with the Compose plugin (`docker compose` v2+), **or** Podman with `podman compose`

Cockpit ships with Fedora and most RHEL-based systems; elsewhere, install it and run `sudo systemctl enable --now cockpit.socket`. For rootless Docker or Podman, see [Podman Compatibility](docs/wiki/Podman-Compatibility.md).

## Installation

The prebuilt packages below are from the original project and do not include changes made in this fork.

**Arch Linux**

```bash
paru -S cockpit-compose
```

**Fedora / RHEL / CentOS Stream / openSUSE**

```bash
curl -LO https://github.com/averyfreeman/cockpit-podman-docker-compose/releases/latest/download/cockpit-compose-latest.rpm
sudo rpm -i cockpit-compose-latest.rpm
```

**Debian / Ubuntu / Linux Mint / Pop!\_OS**

```bash
curl -LO https://github.com/averyfreeman/cockpit-podman-docker-compose/releases/latest/download/cockpit-compose-latest.deb
sudo apt install ./cockpit-compose-latest.deb
```

<details>
<summary><b>Manual install</b></summary>

```bash
curl -LO https://github.com/averyfreeman/cockpit-podman-docker-compose/releases/latest/download/cockpit-compose-latest.tar.gz
curl -LO https://github.com/averyfreeman/cockpit-podman-docker-compose/releases/latest/download/cockpit-compose-latest.tar.gz.sha256
sha256sum -c cockpit-compose-latest.tar.gz.sha256
tar -xzf cockpit-compose-latest.tar.gz
sudo mkdir -p /usr/share/cockpit/cockpit-compose
sudo cp -r cockpit-compose/* /usr/share/cockpit/cockpit-compose/
```

</details>

Then reload Cockpit — **Docker Compose** appears in the left navigation.

## Translations

The UI follows Cockpit's language setting.

<!-- i18n-coverage-start -->
| Coverage | Languages |
|---|---|
| 100% | English (`en`) — source, `ar`, `cs`, `de`, `es`, `fi`, `fr`, `he`, `id`, `it`, `ja`, `ka`, `ko`, `nl`, `pl`, `pt-BR`, `ro`, `ru`, `sk`, `sv`, `tr`, `uk`, `zh-CN`, `zh-TW` |
<!-- i18n-coverage-end -->

To add a language, copy `src/i18n/locales/en.json`, translate the values, and register it in `src/i18n/index.ts`.

## Development

```bash
git clone https://github.com/averyfreeman/cockpit-podman-docker-compose.git
cd cockpit-compose
npm install
npm run build
```

Requires Node.js 22+. Built on [`@rxtx4816/cockpit-plugin-base-react`](https://github.com/RXTX4816/cockpit-plugin-base-react). See [CONTRIBUTING.md](CONTRIBUTING.md) for live reload, tests, commit conventions and working on the base library, and [VM Testing](docs/wiki/VM-Testing.md) for the QEMU test VMs.

Bugs and feature requests go to [GitHub Issues](https://github.com/averyfreeman/cockpit-podman-docker-compose/issues). Security issues: please report privately — see [SECURITY.md](SECURITY.md).

## Versioning

Releases follow [semantic versioning](https://semver.org): patch releases fix bugs, minor releases add features, and anything that breaks existing setups waits for a new major version. See [Releases](https://github.com/averyfreeman/cockpit-podman-docker-compose/releases) for what changed in each version.

## License

[AGPL-3.0-only](LICENSE) © 2025–2026 RXTX4816. Earlier releases were MIT — see [LICENSE-HISTORY.md](LICENSE-HISTORY.md). Bundled third-party licenses are listed in [THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt).
