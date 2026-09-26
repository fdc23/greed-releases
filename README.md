# GreedOT Releases

Official public binary distribution repository for GreedOT.

Source authority lives separately in `fdc23/greedot`. This repository contains versioned release artifacts, checksums, release metadata and future update manifests. Published artifacts are not editable source.

## Current channel

GreedOT is operating in **ALPHA OPEN** on the public prerelease channel.

```text
CURRENT_LINUX_RELEASE=v1.0.0-rc.2
CURRENT_WINDOWS_RELEASE=v1.0.0-rc.1
CHANNEL=PRERELEASE
OPERATING_PHASE=ALPHA_OPEN
STABLE_V1_0_0=NOT_DECLARED
```

Current public client set:

- Linux x86_64 updater-capable encrypted bootstrap: `v1.0.0-rc.2`;
- Windows x86_64 portable package: `v1.0.0-rc.1`;
- checksums;
- macOS is pending and must not be advertised as available until native acceptance is complete.

## Current accepted assets

Linux:

- `GreedOT-Linux-x86_64-alpha-updater-bootstrap-39b8bd677afc.tar.gz`
- SHA256 `ce586872638053e8141729f4b37ed494dd6d8ab222b2490fd866060f4557d7ad`
- release `v1.0.0-rc.2`
- public updater endpoint `https://greed.cl/client-updates/alpha/linux-x64.json`
- encrypted resource updater / public-origin acceptance: PASS
- Linux executable self-update acceptance: pending

Windows:

- `GreedOT-Windows-x86_64-a3c-2857f01d157a-p13-fullmap.zip`
- SHA256 `3194a0f98fa907db6d17ff05e7371011405ba7fb0bac63c0c7063e74d1ddf625`
- release `v1.0.0-rc.1`

The Linux updater bootstrap publication and public-origin acceptance are closed. Windows updater/bootstrap acceptance remains a separate later workstream.

## Release model

GreedOT uses one product line across platforms, while platform acceptance may advance at different release-candidate checkpoints.

A release may contain:

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

The accepted Linux client consumes the HTTPS Alpha updater manifest, compares exact published resource bytes by SHA-256, installs encrypted resource payloads, and restarts when a restart-required resource changes. Linux executable self-update is not yet accepted.

## macOS

macOS is the principal pending platform. The production target is a native Cocoa/AppKit Universal 2 application. XQuartz is not an accepted production dependency.
