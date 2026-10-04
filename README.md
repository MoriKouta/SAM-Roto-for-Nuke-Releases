# SAM Roto for Nuke v1.0.1

Point-guided AI roto inside Nuke. Select multiple subjects, track and correct their mattes,
refine edges with optional ViTMatte, then use Nuke alpha and Write.

## Start in a few steps

Download and extract the ZIP → save work and close Nuke/backend → **install_windows.bat / install_linux.sh**
→ **Install SAM Roto → automatic Full Setup → Finish** → restart Nuke.
Select a Source in the Node Graph → **Tab → search “SAM Roto” → SAM Roto**.
A connected Group is created and its Properties open → **Open Editor → Prepare Source**.
Without a selected Source, the command shows guidance and creates no node.
The upper **SAM Roto → Open SAM Roto** menu remains available.
Start with **Full Range / Local Cache / Auto**. No system Python, Git or startup editing.

## Select

Choose an Object, add foreground points with **Add Point**, then create another Object for a separate subject.

![Select — frame 1: Add Point guidance for two objects, shown in red/yellow overlay.](docs/images/select_1.png)

*Select — frame 1: Add Point guidance for two objects, shown in red/yellow overlay.*

## Track

**Track** unfinished frames. Scrub, add correction points and use **Update Track** for existing results.

![Track — frame 24: two object overlays; Status shows 24 frames completed.](docs/images/track_2.png)

*Track — frame 24: two object overlays; Status shows 24 frames completed.*

## ViTMatte OFF / ON

Inspect the same frame in **Matte View** and toggle optional **ViTMatte** to compare edge refinement.

| ViTMatte OFF · frame 24 | ViTMatte ON · frame 24 |
| --- | --- |
| <img src="docs/images/vitmatte_off_3.png" alt="ViTMatte OFF — frame 24, Matte View." width="460"> | <img src="docs/images/vitmatte_on_3.png" alt="ViTMatte ON — frame 24, Matte View; compare the displayed edges with OFF." width="460"> |

*Same displayed frame in Matte View: compare the edges. This example is not a guarantee for every shot.*

## Cutout / output

Use **Cutout View** to inspect the current-frame matte. In Nuke, inspect **rgba.alpha**, connect **Write**
and render; required Final Mattes prepare before the GUI Render continues automatically.

![Cutout — frame 24 current-frame preview. Final mattes are paused at 9/24; this is not a completed Write.](docs/images/complete_4.png)

*Cutout — frame 24 current-frame preview. Final mattes are paused at 9/24; this is not a completed Write.*

User-provided operation examples captured in a development checkout displaying v1.0.0 (build 2f574ca). These are not native acceptance evidence for the published v1.0.0 ZIP (a2545b9). The Cutout shows the current frame, not all Final Mattes or a completed Write.

## Download / guides

**[Latest release / download](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/latest)** · **[English install / usage guide](docs/QUICKSTART_EN.md)** ·
**[日本語ガイド](docs/QUICKSTART_JA.md)**

Download the versioned ZIP from the latest Release assets. Current published version: **[v1.0.1 ZIP](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/download/v1.0.1/SAM-Roto-for-Nuke-v1.0.1.zip)**.
Native Full Fresh Install, Tab/Properties, installer progress UI and GPU acceptance remain unverified for v1.0.1.

Full Setup prepares Python/PyTorch, SAM 2/2.1 Base+ and ViTMatte models; they run locally afterward.
Compatible updates preserve runtime/models and artist data. The guide includes the actual v1.0.0 Install / Finish screens.

## Requirements / limitations

- **Windows / Linux x86_64 · NVIDIA CUDA-capable GPU required.** Internet for install/repair.
- Allow 20 GB free during standard setup, plus shot caches; GPU memory needs depend on the shot.
- Nuke 15.2 / 16.0 / 16.1 / 17.x are compatibility targets. Validation is not complete for every OS/Nuke/GPU combination.
- macOS, CPU-only / AMD-only / Intel-only inference are unsupported in v1.0.1.
- Windows SAM3/3.1 is unavailable; Linux is experimental and needs installer Advanced + approved HF access.
- Farm/terminal renders require prepared caches/runtime or baked standard nodes. No automatic farm inference.
- Get Color and Ctrl+Shift+C custom hotkey are not included.

For a CUDA/backend problem, use **Support → Logs / Copy Diagnostics**. The physical cause of the reported
SAM2.1 Add Point CUDA unknown error remains unconfirmed. Review attachments for confidential information.
**Support → Check for Updates** is manual; it does not automatically install updates.
Development checkouts keep **DEV Sync + Reload**; do not install over your normal DEV profile.

## Guides / screenshots

[English](docs/QUICKSTART_EN.md) · [日本語](docs/QUICKSTART_JA.md) ·
[Detailed installation / recovery](docs/INSTALLATION.md) · [v1.0.1 release notes](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/tag/v1.0.1) ·
[Image URLs / captions](docs/SCREENSHOTS.md)

The guides also retain actual v1.0.0 installer captures.

## Integrity / licenses

ZIP SHA-256: `6768e3f7ccb3e3b8d495bea66699719ade40c25f9532fd5d75a3833fe6fef2a1`.
Application source: `37e79965aa514d6be9ad06a8ee2cc13f3b82972f` · 39,352,403 bytes (v1.0.1 ZIP).
Manual checksum comparison is optional; internal application/uv/source checks remain mandatory.
Some embedded ZIP docs retain preparation-stage candidate wording; the [published v1.0.1 Release](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/tag/v1.0.1) and checksum identify the artifact.
Original SAM Roto code is MIT; third-party components retain their own terms.
[LICENSE](LICENSE) · [Third-party notices](THIRD_PARTY_NOTICES.md) · [Pinned inventory](docs/THIRD_PARTY_INVENTORY.md).
