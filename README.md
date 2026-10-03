# SAM Roto for Nuke v1.0.0

[日本語](README_JA.md) · [Release / Download](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/tag/v1.0.0)

Point-guided AI roto inside Nuke. Multiple objects, Track/correction, Global Adjustment,
Object Overrides, optional ViTMatte, direct alpha/Write output and automatic Final preparation.

## Requirements

Windows / Linux x86_64 · NVIDIA CUDA-capable GPU required.
macOS, CPU-only, AMD-only and Intel-only inference are not supported in v1.0.0.
Nuke 15.2 / 16.0 / 16.1 / 17.x are compatibility targets; native v1.0.0 GUI/GPU validation is pending.
Pending native evidence is preserved separately from the maintainer's publication decision.

## Install / update

1. Download **SAM-Roto-for-Nuke-v1.0.0.zip** from the Release.
2. Extract and open the SAM-Roto-for-Nuke folder.
3. Close Nuke/backend. Run **install_windows.bat** or **install_linux.sh**.
4. Install SAM Roto → automatic Full Setup → Finish.
5. Restart Nuke → **SAM Roto → Open SAM Roto**.

No system Python/Git, environment edits or startup-file editing. Full Setup prepares pinned Python/PyTorch,
SAM 2/2.1 Base+ and ViTMatte, verifies hashes and local-only loading. Standard Point/Track/ViTMatte needs
no first-use download. Repair handles incomplete components. Updates preserve compatible runtime/models
and artist cache/Points/State/tracking; cancellation/failure rolls back owned changes.

Use the same installer with Nuke/backend stopped for updates. Normal development checkouts retain DEV
Sync + Reload; this public installer is not a way to update a developer's normal profile.

[Install / recovery](docs/INSTALLATION.md) · [Release notes](docs/RELEASE_NOTES_1.0.0_EN.md)

## Known limitations

- Windows SAM3/3.1 is disabled; Linux is experimental and requires installer Advanced + approved HF access.
- Native Windows/Linux GUI/GPU acceptance is pending; automated tests do not certify it.
- Physical cause of the reported SAM2.1 Add Point CUDA unknown error is unconfirmed; recovery/diagnostics are included.
- No Get Color or Ctrl+Shift+C custom hotkey. Farm/terminal renders require prepared caches/runtime or baked nodes.
- Hardware/shot-dependent GPU memory, quality and performance; ViTMatte increases GPU load.

Support → Check for Updates is manual. Support → Copy Diagnostics provides sanitized reporting.
The fixed ZIP retains preparation-time Draft wording in some embedded documents; this Release page and
its checksum identify the published artifact. No native pending value was changed to PASS.

## Artifact identity / licenses

Application commit: `a2545b988bc86b57dffc145c9f9bcad87508c663`.
ZIP SHA-256: `12d9f0d090937cffc9b17a6f170c686b607283607d8d1ba5bab579dd59ab02fb`.
SHA-256 comparison is optional advanced verification. Internal uv/source/application checks remain mandatory.
Original SAM Roto code is MIT; third-party components retain their own terms.
[Notices](THIRD_PARTY_NOTICES.md) · [Pinned inventory](docs/THIRD_PARTY_INVENTORY.md).

This repository contains distribution documentation and approved release assets, not development history.
Old Internal RC packages are not part of public distribution.
