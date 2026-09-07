# Cuedrift — downloads & updates

Downloads for the **Cuedrift** macOS app, and the update feed the app reads
to check for new versions.

This repo holds no source code. It exists because Cuedrift's source repo is
private, and a private repo's release assets can't be fetched by a shipped
app.

## Download

Grab the latest `Cuedrift.dmg` from
[Releases](https://github.com/steijehillewaert/cuedrift-releases/releases/latest).

Builds are ad-hoc signed but **not notarized**, so the first launch hits
macOS's "Apple could not verify this app" prompt. To get past it once:

1. Open the DMG and drag Cuedrift to Applications.
2. Launch it. When macOS blocks it, open **System Settings ▸ Privacy &
   Security**, scroll to the bottom, and click **Open Anyway**.
3. Launch again and confirm.

macOS 13 or later. Cuedrift runs free for 7 days, then needs a license key.

## Updating

Once you're on 1.96 or later, Cuedrift updates itself: it checks here once
a day, and **Cuedrift ▸ Check for Updates…** checks on demand. Updates are
never installed unattended — the app tells you one is available, and
downloading and installing are separate clicks.

Coming from 1.95 or earlier? Those builds have no updater, so download the
DMG above once. After that it's over the air.

## Release assets

| Asset | What it is |
|---|---|
| `Cuedrift.dmg` | The installer most people want |
| `Cuedrift.app.zip` | The same app, zipped — what the in-app updater downloads |
| `latest.json` | Update manifest: version, download URL, SHA-256 |
| `latest.json.sig` | Ed25519 signature over `latest.json` |

The app verifies that signature against a public key compiled into it
before acting on a manifest, and checks the download against the SHA-256
the manifest pins. An update that fails either check is discarded.

## Issues

Bug reports and feature requests are welcome in
[Issues](https://github.com/steijehillewaert/cuedrift-releases/issues).
