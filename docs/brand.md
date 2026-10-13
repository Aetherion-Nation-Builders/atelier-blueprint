# The brand layer

Atelier Blueprint is CADCraft with a different name on the door. We keep the change small on
purpose: upstream lands many changes a day, and every file we touch is a file that can conflict
when we pull them in. So:

**Renamed (what a person sees):** the window and tab title, the Start page, the macOS app menu
(About, Join the Nation, Hide, Quit), the Help menu and About (where Blueprint comes from, the
Nation, this repository), the close prompt, UI messages in the UI crate and the apps, the
Ukrainian translations of all of these, the PDF Creator and Producer, Windows file properties, the
MCP server title, instructions, connection messages and screenshot tool text, installer and
package names, vendor and links, the browser page, the app icon, and where settings and logs live
(`~/Library/Application Support/Atelier Blueprint`, `%APPDATA%\Atelier Blueprint`).

**Not renamed (machine names):** crate names (`cadcraft-*`), the binaries (`cadcraft`,
`cadcraft-cli`) and the version line they print, command ids (the Nation link keeps the
`ui.discord` id), the eframe app name, the `ai.storyteller.cadcraft` app id and icon file names in
packaging, the built-in "CADCraft Stroke" drafting font (drawings name it), the Windows ProgId
(`CADCraft.Drawing`), registry keys and upgrade code, environment variables (`CADCRAFT_*`), the
Linux settings folder, and the docs under `docs/`.

## Where the name lives

| Place | File |
|---|---|
| English UI strings | literal `"Atelier Blueprint"` in `crates/ui-egui/src` and `apps/` |
| Ukrainian translations | `crates/ui-egui/src/i18n/uk.tsv` (rows keyed by the English strings above) |
| About | `crates/ui-egui/src/dialogs.rs` (`about`) |
| Title bar and Start page | `crates/ui-egui/src/chrome.rs` |
| Menus | `crates/ui-egui/src/menus.rs`, `apps/cadcraft/src/native_menu.rs` (macOS app menu, Nation link) |
| Settings and log folders, window title | `apps/cadcraft/src/main.rs` |
| PDF Creator and Producer | `crates/io/src/pdf.rs` |
| MCP | `crates/mcp/src/{server,backend,tools}.rs` |
| Windows file properties | `apps/cadcraft/build.rs` |
| macOS bundle | `packaging/macos/Info.plist.in` (display name, copyright; identifier unchanged) |
| Windows installer | `packaging/windows/cadcraft.wxs` (name, manufacturer, links, install folder, shortcuts; ProgId, registry keys and upgrade code unchanged), and the signing description in `sign.ps1` |
| Linux desktop entry, AppStream, nfpm | `packaging/linux/ai.storyteller.cadcraft.*`, `nfpm.yaml` |
| Browser build | `apps/cadcraft-web/index.html`, `apps/cadcraft-web/src/main.rs` |
| README and NOTICE | README: our header above upstream's feature sections; NOTICE: ours on top of theirs, kept on merge by `.gitattributes` |
| App icon | `assets/app-icon/` (ours: `cadcraft.svg` is the master; rows in `ATTRIBUTION.md`) |

Still upstream's name, for later passes: messages from the engine and file-format crates (for
example "Not saved (CADCraft can't write these object types yet)"), and the `docs/` manuals.
For the packaging pass (real installers): the macOS `.app` bundle and DMG names
(`packaging/macos/package.sh`), the DMG background (`packaging/macos/dmg/`, which still shows the
old icon and name), the package scripts' file names, the Linux package maintainer, the AppStream
brand colours and screenshot, and the release titles in `release.yml`.
