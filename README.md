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
- **Version selector**: the version number on the download panel is a drop-down (a paper label like the language one, and a list with each version's date; it takes each version's look). Picking a version (or `?v=0.3.0`, or "See this version" in the history) shows its notes, downloads and controls, and restyles the page as that version: 0.4.0 keeps the page's own cardboard look below, with `media/hero-*` and the screenshots in `screenshots/` (and so does any newer version until it gets a look of its own); the earlier ones look like the game's menus back then, with their own background video and screenshots. The looks live in `LOOKS` in `index.html`: `proto` (0.1–0.2, Godot's default theme over the first menu's navy) and `navy` (0.3, the navy theme of `ui_theme.gd` back then); each has its video and poster in `media/vX.Y.Z/` (recorded from that version's commit) and its screenshots in `screenshots/vX.Y.Z/`. Each earlier version's video and screenshots show what it brought (0.1: four movers, the bumpy truck and the pay screen; 0.2: spinning, kicking and bumping into each other; 0.3: the pool, kicks and the chat), and a few small drawings of it peek out next to the panels on wide screens (`.deco`). The controls list knows which keys each version had (`CONTROLS`, with the version each one appeared and went away).
- The current version's look is the game's menus (cardboard panels with packing tape, paper-label buttons, Lilita One). Behind the top runs `media/hero-1080.webm` / `.mp4` (or the `-720` ones on small screens), a 60 fps loop of the menu's background scenes recorded from the game; it is not downloaded when the visitor asks for reduced motion or to save data (then `media/hero-poster.webp` shows and a button plays it), and it pauses when scrolled out of view. Below it, the page is the house floor (the game's wood texture, `media/floor.webp`) with some of the game's props seen from above (`media/props/`) peeking out between the panels on wide screens. Screenshots open in a viewer on the same page.

## Publishing a new version

1. In the game project, export the three presets (Windows Desktop, Linux, macOS) into `build/`.
2. Create a release with a tag like `v0.4.0` and attach the three files with the names above. The first line of the notes is shown in bold; lines starting with `- ` become a list.
3. Add the notes of that version, translated into the 12 languages, and its date to `release-notes.json`. The page shows them in the visitor's language (falling back to English, then to the release notes on GitHub).
4. In `index.html`, set `PUBLISHED` to the new tag. A new version shows the cardboard look of 0.4.0 until it gets a look of its own: then give it its entry in `LOOKS` with its media in `media/vX.Y.Z/` and `screenshots/vX.Y.Z/` (0.4.0 keeps the root ones).

## Languages

The page detects the visitor's language (English, Español, Português, Français, Deutsch, Italiano, Polski, Türkçe, Русский, 中文, 日本語, 한국어) and remembers the one picked in the selector. `?lang=xx` forces one and `?os=windows|macos|linux` forces a system. Release notes come translated from `release-notes.json`.

## Local preview

Open `index.html` directly (or add `?demo`) to see it with sample data; `?demo=next` also adds a sample 0.5.0 to see the cardboard look.
