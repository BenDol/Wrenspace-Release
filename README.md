<div align="center"><img src="https://wrenspace.ai/assets/img/wrenspace-mark.svg" height="128"></img></div>
<h1 align="center">Wrenspace</h1>

<p align="center"><strong>Agent Super Harness.</strong> Many minds. One direction.</p>

<p align="center">
  <a href="https://wrenspace.ai">wrenspace.ai</a> &middot;
  <a href="https://wrenspace.ai/download">Download</a> &middot;
  <a href="https://account.wrenspace.ai">Account</a> &middot;
  <a href="https://wrenspace.ai#pricing">Pricing</a>
</p>

---

This repository hosts the **published Wrenspace desktop builds**. It contains no source code: every release here is produced and verified by the private build pipeline, then mirrored to this repo. The in-app auto-updater reads these releases directly.

Wrenspace docks multiple AI-agent CLI sessions (Claude Code, OpenAI Codex, Cursor Agent, xAI Grok Build, Moonshot Kimi Code, OpenCode, Nous Hermes, plus custom adapters) in one configurable grid, and keeps sessions, worktrees, plugins and project context connected around them.

## Download

| Platform | Stable | Staging Edge |
|---|---|---|
| Windows 10/11 (x64) | [Installer](https://api.wrenspace.ai/v1/downloads/latest/windows) | [Installer](https://api.wrenspace.ai/v1/downloads/staging-edge/windows) |
| macOS (Universal, Intel + Apple silicon) | [DMG](https://api.wrenspace.ai/v1/downloads/latest/mac) | [DMG](https://api.wrenspace.ai/v1/downloads/staging-edge/mac) |
| Linux (x64) | [AppImage](https://api.wrenspace.ai/v1/downloads/latest/linux) | [AppImage](https://api.wrenspace.ai/v1/downloads/staging-edge/linux) |

Those links resolve to the exact installer named in the release's own update manifest, so they never go stale after a version bump. Prefer a specific build, or need the `.deb` / `.rpm`? Pick it straight off the [Releases](https://github.com/BenDol/Wrenspace-Release/releases) page.

## Release channels

| Channel | Tag | Who it is for | Backend |
|---|---|---|---|
| **Stable** | `vX.Y.Z` (marked *Latest*) | Everyone | Production |
| **Staging Edge** | `staging-edge` | External testers, permanently pre-release | Staging API, test billing |
| **Bleeding Edge** | `bleeding-edge` | Early builds off the main branch | Production |

Every build published here has passed the cross-platform verification matrix (Windows, macOS, Linux) before it is mirrored. A build that had to ship without that gate is stamped with a "verification skipped" banner in its release notes and a `verification-skipped.json` asset, so you can always tell.

**Staging Edge installs side by side** with a stable install as *Wrenspace (Staging)*: its own shortcut, its own data directory, its own account environment. It talks to the staging backend with test billing, so a stable subscription does not carry over to it. You can switch a staging install between the `staging-edge` and `bleeding-edge` feeds under **Settings > Updates**.

## Install

**Windows.** Run the `-Setup.exe`. It installs per user, so no administrator prompt. The installer is Authenticode signed; the updater additionally refuses any update whose signer does not match.

**macOS.** Open the `.dmg` and drag Wrenspace to Applications. Builds are signed and notarized by Apple, so Gatekeeper opens them without a warning.

**Linux.** Take whichever suits your distro:
- `.AppImage`: `chmod +x Wrenspace-*.AppImage && ./Wrenspace-*.AppImage`
- `.deb`: `sudo apt install ./Wrenspace-*.deb`
- `.rpm`: `sudo dnf install ./Wrenspace-*.rpm`

## Updating

Wrenspace updates itself from this repository. It checks the channel you are on at launch and on a schedule, downloads in the background, and installs on your say-so. There is nothing to configure for stable installs.

Windows (PowerShell):

```powershell
(Get-FileHash .\Wrenspace-<version>-Setup.exe -Algorithm SHA256).Hash.ToLower()
Get-Content .\Wrenspace-<version>-Setup.exe.sha256
```

macOS / Linux:

```bash
shasum -a 256 Wrenspace-<version>.dmg
cat Wrenspace-<version>.dmg.sha256
```

The two values must match. The channel `.yml` manifest carries the same files' SHA-512 digests, which is what the auto-updater checks on every download.

## Before you start

- **A Wrenspace account.** The app signs you in on first launch. Manage the subscription and your devices at [account.wrenspace.ai](https://account.wrenspace.ai).
- **At least one agent CLI.** Wrenspace drives the CLIs you already use. Claude Code and OpenAI Codex are the built-in defaults; Cursor Agent, Grok Build, Kimi Code, OpenCode and Hermes are optional providers you can turn on, and a custom adapter covers anything else.

## Support

Issues are disabled on this mirror because it carries binaries only. To report a problem:

1. Use **Report an issue** at the bottom of the Settings sidebar inside Wrenspace. It can attach your logs and system info, and files the report for you.
2. Or email [hello@wrenspace.ai](mailto:hello@wrenspace.ai).

## Legal

Wrenspace is published by B. Dol Technical Consulting, LLC. The binaries in this repository are distributed under the Wrenspace [Terms of Service](https://wrenspace.ai/terms); see also the [Privacy Policy](https://wrenspace.ai/privacy). This repository is not open source and grants no licence to redistribute or modify the builds it hosts.
