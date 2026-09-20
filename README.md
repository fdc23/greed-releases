# GreedOT Releases

Official public binary distribution repository for GreedOT.

Source authority lives separately in `fdc23/greedot`. This repository contains versioned release artifacts, checksums, release metadata and future update manifests. Published artifacts are not editable source.

## Current channel

GreedOT is operating in **ALPHA OPEN** on the public prerelease channel.

```text
CURRENT_RELEASE=v1.0.0-rc.1
CHANNEL=PRERELEASE
OPERATING_PHASE=ALPHA_OPEN
STABLE_V1_0_0=NOT_DECLARED
```

The current release contains:

- Linux x86_64 portable package;
- Windows x86_64 portable package;
- checksums;
- macOS is pending and must not be advertised as available until native acceptance is complete.

## Current accepted assets

Linux:

- `GreedOT-Linux-x86_64-a3c-2857f01d157a-p13-fullmap.tar.gz`
- SHA256 `3d7706a8c4238c57347dcbaaff59bf38acc46c7a10cdf759014cc4db83902c1b`

Windows:

- `GreedOT-Windows-x86_64-a3c-2857f01d157a-p13-fullmap.zip`
- SHA256 `3194a0f98fa907db6d17ff05e7371011405ba7fb0bac63c0c7063e74d1ddf625`

The Linux public-download acceptance is closed. Windows build, encryption, packaging and release publication are closed; a separate fresh external-download acceptance receipt remains unrecorded.

## Release model

GreedOT uses one product version across platforms. A release may contain:

- Linux x86_64;
- Windows x86_64;
- macOS Universal 2 when accepted;
- platform checksum sidecars;
- aggregate checksums;
- update manifests when the updater contract is activated.

A prerelease publication does not imply:

- PayPal Live enabled;
- stable `v1.0.0`;
- final production closeout.

## Immutable release rule

Published assets are immutable.

Any distributed change to executable, map/minimap, modules, assets, launcher, packaging behavior or platform support receives a new release version/tag. Never silently replace an existing asset under the same release version.

## Portable profile policy

GreedOT intentionally keeps `profile/` inside the portable installation directory.

Do not migrate profile state to hidden platform-specific directories unless a later explicit architecture decision supersedes this contract.

Updates must distinguish replaceable release state from mutable player state. Existing player configuration/preferences must be preserved, while a new authoritative revisioned minimap may be seeded when required.

## Update policy

The client must never update itself with `git pull`.

A future updater should consume an HTTPS release manifest, compare versions, select the current platform artifact, verify checksum/signature, stage it, and apply the update atomically while preserving mutable player state. Initial updater implementation should prefer full-package updates.

## macOS

macOS is the principal pending platform. The production target is a native Cocoa/AppKit Universal 2 application. XQuartz is not an accepted production dependency.
