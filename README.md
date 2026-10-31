# 🧀 Crispy Launcher

A desktop launcher that installs, prepares and starts the Rust Minecraft client — the Horizon
launcher, rebranded to **Crispy Launcher**, with its look kept under our control so an upstream
update cannot put the old UI back.

Download it from [the releases page](https://github.com/Web-mc1/CrispyLauncher/releases) (Windows
installer, Linux AppImage) or from the [website](https://web-mc1.github.io/CrispyLauncher/).

**You need** a Microsoft account that owns Java Edition, and a GPU with Vulkan or OpenGL 3.3
(Linux), Vulkan or DirectX 12 (Windows), or a Mac on Apple Silicon. If you already have a
Minecraft install (official launcher, Prism, MultiMC…) it is reused; without one, Play downloads
the game from Mojang for your account.

## What it does

- **Versions** — lists the builds it can install, downloads one, and removes it again.
- **Play** — prepares the game from your own copy of Minecraft and starts it, as you.
- **Accounts** — signs in with Microsoft, checks Java Edition ownership, and keeps the session in
  the OS keychain (Keychain, Credential Manager, Secret Service).
- **Mods, modpacks, servers** — browse and install, import a Java modpack, host a world for friends.

Step by step: [launcher/README.md](launcher/README.md).

## Run it from source

The launcher is its own Cargo workspace, built with [GPUI](https://www.gpui.rs):

```bash
cd launcher && cargo run --release
```

## Updating without losing the UI

```bash
git remote add upstream https://github.com/horizon-rust/horizon.git
./scripts/sync-upstream.sh
```

The script fetches upstream, merges it, restores our version of every path in
[crispy-ui.txt](crispy-ui.txt), re-applies the rebrand to the strings upstream added, and records
the merge as one commit. The launcher's own self-updater is switched off in
`launcher/src/backend.rs`, because it used to replace this binary with upstream's — wiping the UI.
Details: [docs/upstream-sync.md](docs/upstream-sync.md) and [CRISPY.md](CRISPY.md).

## Credits

A fork of [horizon-rust/horizon](https://github.com/horizon-rust/horizon), MIT licensed. The
original copyright notices stay: [LICENSE](LICENSE) and [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)
must ship with every copy.

Not an official Minecraft product, nor approved by or associated with Mojang or Microsoft. This
repository contains no Minecraft code, assets or data.
