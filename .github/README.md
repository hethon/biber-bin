# biber-bin

Unofficial redistribution of [biber](https://github.com/plk/biber)'s binaries on GitHub Releases, with one-line installers.

## Install

**Linux / macOS:**

```bash
curl --proto '=https' --tlsv1.2 -LsSf https://github.com/hethon/biber-bin/releases/latest/download/installer.sh | sh
```

**Windows (PowerShell):**

```powershell
powershell -ExecutionPolicy Bypass -c "irm https://github.com/hethon/biber-bin/releases/latest/download/installer.ps1 | iex"
```

> [!NOTE]
> The install scripts are generated with [ingen](https://github.com/hethon/ingen). They download the build for your platform from this repo's [releases](https://github.com/hethon/biber-bin/releases), verify its checksum, and install it to a user-local bin directory (`$HOME/.local/bin` on Linux and macOS). The scripts are attached to every release.

Then check that it works:

```bash
biber --version
```

> [!NOTE]
> The first run is slower: biber unpacks itself into a cache directory. `biber --cache` prints where.

## Supported platforms

Linux (x86_64, i686, musl x86_64), macOS (Intel and Apple Silicon, via the universal build), Windows (x86_64, i686).

Upstream publishes no ARM Linux or FreeBSD builds, so there are none here either.

## Why

**Biber already publishes its binaries on SourceForge, so why republish them on GitHub Releases?**

I wanted one-line installers for biber. [ingen](https://github.com/hethon/ingen), the tool I use to generate them, expects the artifacts to live on GitHub Releases, or at least to have a similar URL structure.

## How releases are made

The [Republish Biber](https://github.com/hethon/biber-bin/actions/workflows/republish.yml) workflow downloads the binaries for a given Biber version from SourceForge, renames them by Rust target triple, and attaches them to a release tagged with that version (for example `v2.17`). Each release page links back to the upstream folder for every file, and GitHub shows a SHA-256 digest for each asset. A tag like `v2.17-1` marks a re-release of the same Biber version.

## Notes

- This repo is a thin packaging layer. The binaries are upstream's, unmodified. Bugs in biber itself belong [upstream](https://github.com/plk/biber/issues).
- These releases track upstream releases starting from version 2.17.
