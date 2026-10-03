# SAM Roto for Nuke v1.0.0

Point-guided AI roto inside Nuke: create multiple object mattes, track and correct them,
refine edges with Adjustment / optional ViTMatte, then use Nuke alpha and Write.

**[Download v1.0.0](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/download/v1.0.0/SAM-Roto-for-Nuke-v1.0.0.zip)** · **[Install / first matte guide](docs/QUICKSTART_EN.md)** ·
**[日本語ガイド](docs/QUICKSTART_JA.md)**

## Start here

1. Download and extract the ZIP.
2. Save work and close Nuke/backend; run **install_windows.bat** or **install_linux.sh**.
3. **Install SAM Roto → Full Setup → Finish**. Restart Nuke.
4. Select a source → **SAM Roto → Open SAM Roto → Prepare Source**.
5. **Add Point → Track → correct with points / Update Track**.
6. Optional **ViTMatte** → inspect **rgba.alpha** → connect **Write** and render.

No system Python, Git or startup editing. Standard Full Setup prepares SAM 2/2.1 Base+ and ViTMatte models;
they run locally afterward. Updates preserve compatible runtime/models and artist data.

![Actual v1.0.0 Full Setup completion](docs/images/finish-v1.0.0.png)

*Windows v1.0.0 installer: Finish, then restart Nuke.*

## Requirements / limitations

- **Windows / Linux x86_64 · NVIDIA CUDA-capable GPU required.** Internet for install/repair.
- Allow 20 GB free during standard setup, plus shot caches; GPU memory needs depend on the shot.
- Nuke 15.2 / 16.0 / 16.1 / 17.x are compatibility targets. Validation is not complete for every OS/Nuke/GPU combination.
- macOS, CPU-only / AMD-only / Intel-only inference are unsupported in v1.0.0.
- Windows SAM3/3.1 is unavailable; Linux is experimental and needs installer Advanced + approved HF access.
- Farm/terminal renders require prepared caches/runtime or baked standard nodes. No automatic farm inference.
- Get Color and Ctrl+Shift+C custom hotkey are not included.

For a CUDA/backend problem, use **Support → Logs / Copy Diagnostics**. The physical cause of the reported
SAM2.1 Add Point CUDA unknown error remains unconfirmed. Review attachments for confidential information.
**Support → Check for Updates** is manual; it does not automatically install updates.
Development checkouts keep **DEV Sync + Reload**; do not install over your normal DEV profile.

## Guides / screenshots

[English](docs/QUICKSTART_EN.md) · [日本語](docs/QUICKSTART_JA.md) ·
[Detailed installation / recovery](docs/INSTALLATION.md) · [Release notes](docs/RELEASE_NOTES_1.0.0_EN.md) ·
[Image URLs / captions](docs/SCREENSHOTS.md)

Installer images show v1.0.0. Editor images in the guide show a **private 1.0.1 update-test fixture**
displaying saved synthetic mattes; they are not formal v1.0.0 screenshots or new inference/Write evidence.

## Integrity / licenses

ZIP SHA-256: `12d9f0d090937cffc9b17a6f170c686b607283607d8d1ba5bab579dd59ab02fb`.
Application commit: `a2545b988bc86b57dffc145c9f9bcad87508c663` · 39,337,331 bytes.
Manual checksum comparison is optional; internal application/uv/source checks remain mandatory.
Some embedded ZIP docs retain preparation-time Draft wording; this published Release identifies the artifact.
Original SAM Roto code is MIT; third-party components retain their own terms.
[LICENSE](LICENSE) · [Third-party notices](THIRD_PARTY_NOTICES.md) · [Pinned inventory](docs/THIRD_PARTY_INVENTORY.md).
