# Cuedrift — downloads & updates

Downloads for the **Cuedrift** macOS video playout app, and the update feed
the app reads to check for new versions.

This repo holds no source code. It exists because Cuedrift's source repo is
private, and a private repo's release assets can't be fetched by a shipped
app.

## Download

Grab the latest `Cuedrift.dmg` from
[Releases](https://github.com/steijehillewaert/cuedrift-releases/releases/latest),
open it, and drag Cuedrift to Applications.

From **2.0 onwards** the app and the disk image are signed with a Developer
ID and notarized by Apple, so they open normally — no Gatekeeper prompt and
no trip through System Settings.

Earlier builds were ad-hoc signed and are blocked on first launch with
"Apple could not verify this app". If you're on one of those, the fix is to
download 2.0 or later rather than to work around the warning.

Requires macOS 13 or later. Cuedrift runs free for 7 days, then needs a
license key.

## Updating

From 1.96 onwards Cuedrift updates itself: it checks here once a day, and
**Cuedrift ▸ Check for Updates…** checks on demand.

Nothing is installed unattended. Cuedrift is usually running a show when
it's open, so an update that swapped the app out mid-playlist would be worse
than a stale version — the app tells you one is available, and downloading
and installing are separate, deliberate clicks. Installing quits and
reopens the app.

Coming from 1.95 or earlier? Those builds have no updater, so download the
DMG above once. After that it's over the air.

## SDI output

Output can go to a Blackmagic device — an UltraStudio, a DeckLink card —
instead of a second display, chosen from the Output dropdown alongside your
screens. Picture is scaled and letterboxed to the video mode's raster, and
programme audio is embedded in the SDI stream.

This needs Blackmagic's
[Desktop Video](https://www.blackmagicdesign.com/support/family/capture-and-playback)
installed. Without it Cuedrift behaves exactly as before and simply offers
no SDI destinations.

## Release assets

| Asset | What it is |
|---|---|
| `Cuedrift.dmg` | The installer most people want |
| `Cuedrift.app.zip` | The same app, zipped — what the in-app updater downloads |
| `latest.json` | Update manifest: version, download URL, SHA-256 |
| `latest.json.sig` | Ed25519 signature over `latest.json` |

The app verifies that signature against a public key compiled into it before
acting on a manifest, and checks the download against the SHA-256 the
manifest pins. An update failing either check is discarded rather than
installed.

## Issues

Bug reports and feature requests are welcome in
[Issues](https://github.com/steijehillewaert/cuedrift-releases/issues).
