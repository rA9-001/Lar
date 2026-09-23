# How Lar works

- **Frontend** — Svelte 5 with SvelteKit (static adapter)
- **Backend** — Rust, via the Tauri v2 command system
- **Privilege escalation** — `pkexec`, triggered only when an action actually needs root
- **No network calls** — everything is read from `/proc`, `/sys`, and local system commands

## Security model

- Fully offline: no telemetry, no analytics, nothing phones home.
- Root access is requested only when actually needed, through `pkexec`.
- All user input is validated against allow-list patterns before reaching system commands.
- Privileged actions are written to an append-only audit log at `$XDG_STATE_HOME/lar/audit.log`.
- Privileged commands are rate-limited.
- Release builds use LTO, a single codegen unit, overflow checks, and symbol stripping.
- The frontend is locked down with a CSP and frozen prototypes.

## Project structure

```
src/                    # Svelte frontend
├── lib/                # Feature components (13 modules)
├── routes/             # SvelteKit pages
├── app.html
└── global.css

src-tauri/              # Rust backend
├── src/
│   ├── lib.rs          # Command registration, rate limiting
│   ├── audit_log.rs    # Append-only audit log
│   ├── cleaner.rs      # System cleanup
│   ├── disk.rs         # Partition & directory analysis
│   ├── distro.rs       # Distribution detection
│   ├── firewall.rs     # UFW wrapper
│   ├── hardening.rs    # Sysctl security hardening
│   ├── hardware.rs     # Hardware info & live stats
│   ├── logs.rs         # journalctl queries
│   ├── network.rs      # Network interfaces & traffic
│   ├── optimizer.rs    # Performance tweaks
│   ├── packages.rs     # Package catalog & installer
│   ├── permissions.rs  # SUID/SGID/world-writable audit
│   ├── services.rs     # systemd management
│   ├── startup.rs      # Autostart entries
│   └── updates.rs      # System updates
├── Cargo.toml
└── tauri.conf.json
```

## IDE setup

[VS Code](https://code.visualstudio.com/) +
[Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode) +
[Tauri](https://marketplace.visualstudio.com/items?itemName=tauri-apps.tauri-vscode) +
[rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer)
