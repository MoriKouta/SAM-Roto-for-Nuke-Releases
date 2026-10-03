# SAM Roto for Nuke v1.0.0

**Published v1.0.0.** The original project code uses MIT; bundled/downloaded components retain their
own terms. Windows/Linux support and pending native validation are disclosed separately from publication
permission. The maintainer's v1.0.0 policy does not require completed native validation on both OS.

[日本語](RELEASE_NOTES_1.0.0_JA.md)

Point-guided AI roto inside Nuke: multiple objects, Track/correction, Global Adjustment,
Object Overrides, optional ViTMatte and direct rgba.alpha/Write output.

## Install / update

Windows/Linux x86_64 with an **NVIDIA CUDA GPU**.
Download SAM-Roto-for-Nuke-v1.0.0.zip, extract, close Nuke/backend, run install_windows.bat
or install_linux.sh → Install SAM Roto → automatic Full Setup → Finish → restart Nuke → SAM Roto → Open SAM Roto.
No system Python/Git or startup edits. Updates preserve compatible runtime/models and artist data.
Full Setup prepares Python/PyTorch, SAM 2/2.1 Base+ and ViTMatte, including pinned hashes and local-only
model loading. Point/Track/ViTMatte need no first-use downloads. Re-run installer Repair for incomplete
components; Cancel/Retry preserves artist data. Windows native UI and Linux desktop/terminal fallback
use the same install transaction. macOS is not supported in v1.0.0.
See [installation and recovery](INSTALLATION.md).

## Known limitations

- v1.0.0 native acceptance remains pending for Nuke 15.2, 16.0, 16.1 and 17.x.
- Windows SAM3/3.1 is disabled; Linux experimental models must be prepared in installer Advanced with approved HF access.
- CPU/AMD-only/Intel-only/macOS inference is unsupported.
- No Get Color or Ctrl+Shift+C custom hotkey.
- Farm/terminal renders need prepared cache/runtime or baked standard nodes; no automatic farm inference.
- Model quality, GPU memory and performance depend on the shot. ViTMatte increases GPU load.

Use Support → Logs / Copy Diagnostics and report short reproduction steps.
Support also offers manual stable-release checks; no automatic update is applied.
Installer log: .nuke/.samroto-bootstrap/install.log. Review attachments for confidential details.

The physical cause of the reported SAM2.1 Add Point CUDA unknown error remains unconfirmed.
