# rootctrl-firmware

Public firmware releases for the **RootCtrl** cuve automation module.

This repository contains **only compiled binaries and release metadata** — the
source code lives in a private repository.

## How it works

- Each tagged release (`vX.Y.Z`) in the private source repo triggers a GitHub
  Action that builds the firmware and publishes here:
  - a GitHub **Release** with `firmware.bin` attached as an asset
  - an updated [`manifest.json`](manifest.json) on `main`
- The RootCtrl device reads `manifest.json` over HTTPS (no auth required),
  compares versions, and pulls the new `firmware.bin` via OTA when the user
  presses **Update now** in the device web UI.

## manifest.json

| field     | meaning                                            |
|-----------|----------------------------------------------------|
| `version` | latest firmware version, e.g. `v1.0.3`             |
| `url`     | direct download URL of `firmware.bin`              |
| `sha256`  | SHA-256 of `firmware.bin` (integrity verification) |
| `size`    | size of `firmware.bin` in bytes                    |
| `notes`   | human-readable release notes                       |

Raw manifest URL used by the device:

```
https://raw.githubusercontent.com/aaponaa/rootctrl-firmware/main/manifest.json
```
