# Get a Move On! — download page

*No job too big.*

Download page for **Get a Move On!**, a co-op moving game with physics for 1–4 players, made with Godot 4.
The game's source code lives in a separate private repository; this one only holds the page and the builds.

Page: https://dreufter.github.io/get-a-move-on-web/

## How it works

- `index.html` is served by GitHub Pages and reads the published **GitHub Releases** of this same repository.
- Every release is a playable version and carries one file per system, always with the same name:
  - `GetAMoveOn.exe` — Windows 64-bit, a single file (no installer, no zip).
  - `GetAMoveOn.x86_64` — Linux 64-bit, a single file (`chmod +x` and run).
  - `GetAMoveOn-macos.zip` — macOS (Intel and Apple Silicon), the `.app` zipped because macOS apps are folders.
- The big button downloads the latest release for the visitor's system (`releases/latest/download/<file>`), even if the GitHub API fails; the other systems are linked right below it.
- Each release shows its notes under "What's new" and, with its three downloads, in the version history.

## Publishing a new version

1. In the game project, export the three presets (Windows Desktop, Linux, macOS) into `build/`.
2. Create a release with a tag like `v0.4.0` and attach the three files with the names above. The first line of the notes is shown in bold; lines starting with `- ` become a list.
3. Add the notes of that version, translated into the 12 languages, and its date to `release-notes.json`. The page shows them in the visitor's language (falling back to English, then to the release notes on GitHub).

## Languages

The page detects the visitor's language (English, Español, Português, Français, Deutsch, Italiano, Polski, Türkçe, Русский, 中文, 日本語, 한국어) and remembers the one picked in the selector. `?lang=xx` forces one and `?os=windows|macos|linux` forces a system. Release notes come translated from `release-notes.json`.

## Local preview

Open `index.html` directly (or add `?demo`) to see it with sample data.
