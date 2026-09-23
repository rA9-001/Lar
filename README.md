# Lar

> *Lar* (Latin) — the household spirit of Roman religion, which looked after the home and
> everything in it.

An all-in-one Linux system utility: the tasks you would otherwise do across a dozen terminal
commands, in one desktop app. Fully offline — no accounts, no servers, no telemetry, no
background services. Built with Tauri v2, Svelte 5 and Rust.

[![release](https://img.shields.io/github/v/release/rA9-001/Lar?sort=semver)](https://github.com/rA9-001/Lar/releases/latest)
[![licence](https://img.shields.io/github/license/rA9-001/Lar)](LICENSE)

## Install

Download from [Releases](https://github.com/rA9-001/Lar/releases/latest), or build from source
below.

## What it does

| Module | |
| --- | --- |
| **System Cleanup** | Scan and remove unused caches, logs and temp files |
| **Disk Usage** | Partition overview with per-directory drill-down |
| **Startup Manager** | XDG autostart entries and systemd user services |
| **System Monitor** | Live CPU, memory and network I/O with rolling history |
| **Performance Optimizer** | sysctl tweaks for CPU, memory, storage, network and kernel — current vs. recommended |
| **Security Hardening** | sysctl protections that persist via `/etc/sysctl.d/` |
| **Firewall Manager** | UFW frontend for rules, policies and status |
| **Network Monitor** | Interfaces, connections, DNS, listening ports, live traffic |
| **Service Manager** | Browse, control and inspect systemd services with inline logs |
| **Permissions Auditor** | SUID/SGID binaries, world-writable files, home directory issues |
| **Package Manager** | Curated catalog (~70 packages), multi-distro, batch install |
| **System Updates** | Package manager and Flatpak (AUR helper detection on Arch) |
| **Log Viewer** | journalctl with filters for priority, unit, boot, time range and grep |

Root is requested through `pkexec`, and only when an action actually needs it.

## Distro support

| Family | Package manager | Tested |
| --- | --- | --- |
| Arch / CachyOS / Manjaro / EndeavourOS | pacman (+ yay/paru) | ✅ |
| Debian / Ubuntu / Pop!_OS / Mint | apt | ○ |
| Fedora / RHEL / CentOS | dnf | ○ |
| openSUSE | zypper | ○ |
| Void Linux | xbps | ○ |
| Alpine | apk | ○ |

✅ tested &nbsp;·&nbsp; ○ should work, not yet tested

## Building

Requires [Rust](https://rustup.rs/) (stable), [Node.js](https://nodejs.org/) 18+, and the
[Tauri v2 system dependencies](https://v2.tauri.app/start/prerequisites/).

```bash
npm install
npm run tauri dev      # development
npm run tauri build    # production -> src-tauri/target/release/
```

## Docs

[How it works](docs/internals.md) — architecture, security model, project layout.

Direct push access is restricted; please [open an issue](https://github.com/rA9-001/Lar/issues)
for bugs or feature requests.

## License

MIT. See [LICENSE](LICENSE).
