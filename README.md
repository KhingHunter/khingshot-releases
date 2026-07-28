# KhingShot releases

Distribution artifacts for **KhingShot**, the macOS capture app. This repository
holds no source code. It exists so that the app's Sparkle updater can reach the
update feed and the installers without a GitHub token.

- **`appcast.xml`** — the Sparkle feed. The running app reads it from
  `https://raw.githubusercontent.com/KhingHunter/khingshot-releases/main/appcast.xml`
  once a day.
- **Releases** — one GitHub Release per version, tagged `v<version>`, with the
  notarized `KhingShot-<version>.dmg` attached. The release body is the
  authored release notes, and the same text is embedded in the appcast item.

Every DMG is signed with Developer ID Application: HUNTER HAYDEN HINTZE
(7SCSY422EQ), notarized by Apple, and stapled. Each appcast enclosure carries an
EdDSA (`sparkle:edSignature`) signature that the app verifies before installing.

Appcast entries are immutable: a shipped `<item>` is never edited or re-signed.
New releases are added ahead of the existing ones.

Source lives in a separate private repository.
