# GreedOT Releases

Official public binary distribution repository for GreedOT.

Source authority lives separately in `fdc23/greedot`. This repository is for versioned release artifacts, checksums, release metadata and update manifests. Production artifacts are never treated as editable source.

## Release model

GreedOT uses one product version across platforms. Platform artifacts are attached to the same GitHub Release:

- Linux x86_64: `.tar.gz`
- Windows x86_64: `.zip` or installer
- macOS: future, when a supported build exists
- `SHA256SUMS`
- `update-manifest.json` when the updater contract is activated

Pre-production public candidates use prerelease tags such as `v1.0.0-rc.1`. Stable production releases use normal semantic-version tags such as `v1.0.0`.

A published release asset is immutable. Any changed map, module, executable or packaged resource receives a new release version instead of silently replacing an existing asset.

## Linux profile policy

The portable Linux distribution intentionally keeps `profile/` inside the GreedOT directory.

This is a product decision: the player can see, inspect, back up and move their profile together with the portable client. Do not migrate it to `~/.local/share/GreedOT/`, AppData or another hidden per-user location without a later explicit architecture decision.

Updates must distinguish between distributable program state and player state:

- program files such as `GreedOT`, `data/`, `modules/`, `mods/` may be replaced by a release;
- existing player settings and mutable profile state must be preserved;
- a new revisioned minimap may be seeded when required by a release;
- a fresh install may include authorized default profile files, including the canonical fully revealed minimap.

## Update policy

The client must never update itself with `git pull`.

A future updater should consume a small HTTPS release manifest, compare versions, download the platform artifact, verify its checksum/signature, stage it, and apply the update atomically while preserving mutable profile state.

Initial updater implementation should prefer full-package updates. Differential patches are deferred until there is evidence they are necessary.

## Current Linux publication candidate

Accepted P13 candidate:

- archive: `GreedOT-Linux-x86_64-a3c-2857f01d157a-p13-fullmap.tar.gz`
- archive SHA256: `3d7706a8c4238c57347dcbaaff59bf38acc46c7a10cdf759014cc4db83902c1b`
- runtime SHA256: `feb0bb05d2d2405bb22ba1098461b4f9725a690502cfa5da0db72afa5e7a4e5b`
- canonical full automap SHA256: `f43a8f95e335a487353b0b70e8db1bf77a190060412eecd1a929322dd1160b76`
- canonical full automap size: `434726` bytes

The first public tag is intended to be `v1.0.0-rc.1`. Public prerelease publication does not by itself declare GreedOT production-ready or enable PayPal Live.
