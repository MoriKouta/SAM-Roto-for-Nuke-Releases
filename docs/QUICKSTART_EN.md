# SAM Roto: select, track and refine your matte

Current release: **v1.1.0**. [Changes / validation limits](RELEASE_NOTES_1.1.0_EN.md).

[日本語](QUICKSTART_JA.md)

Point-guided AI roto inside Nuke. Select each subject with points, track across the shot,
compare optional ViTMatte edge refinement, then use the matte in Nuke.

**Full Setup → Prepare Source → Select → Track / correct → ViTMatte OFF / ON → Cutout → alpha / Write**

Windows / Linux x86_64 and an **NVIDIA CUDA-capable GPU** are required. Nuke 15.2 / 16.0 / 16.1 / 17.x
are compatibility targets; validation is not complete for every OS/Nuke/GPU combination.
Native v1.1.0 GUI/GPU, Fresh Install/Repair and updater exit/restart/data retention remain unverified.
macOS and CPU-only / AMD-only / Intel-only inference are not supported in v1.1.0.
Internet is needed for installation/repair. Allow 20 GB free for standard setup, plus shot caches.

## 1. Download and run Full Setup

1. Download **[SAM-Roto-for-Nuke-INSTALLER.zip](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/latest/download/SAM-Roto-for-Nuke-INSTALLER.zip)** and extract it.
2. Save your work and close all Nuke sessions before installing. Open the extracted folder.
3. Windows: run **install_windows.bat**. Linux: run **install_linux.sh**.
4. Click **Install SAM Roto**. Wait for **SAM Roto is ready**, then click **Finish**.

Current release: **[v1.1.0](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/tag/v1.1.0)**. The fixed Installer URL follows future latest releases.
GitHub Source code ZIPs are not the installer.
Allow approximately **10–30 minutes** for first Full Setup; network, disk and PC conditions can make it longer.

No system Python, Git, pip commands or startup editing. Full Setup downloads Python/PyTorch,
SAM 2 / 2.1 Base+ and ViTMatte models; uv and SAM source archives are already in the ZIP.
Point, Track and ViTMatte use the prepared models locally. Keep the installer for Repair/update.
Linux uses an available desktop UI or a terminal fallback; enable file execution in Properties if needed.

| Install | Finish |
| --- | --- |
| <img src="images/install-v1.0.0.png" alt="v1.0.0 installer with Install SAM Roto button" width="340"> | <img src="images/finish-v1.0.0.png" alt="v1.0.0 Full Setup completion with Finish button" width="340"> |

*Actual Windows v1.0.0 installer and Full Setup completion captures.*

## 2. Open SAM Roto and prepare the Source

Restart Nuke. Select the image/source node, then **Tab → SAM Roto**.
Open the created SAM Roto Group's **Properties → Open Editor**.
On first setup choose:

| Setting | Start with |
| --- | --- |
| Frame Range | **Full Range**; use Project Range / Custom when you only need part of the shot |
| Cache Location | **Local Cache (Recommended)** |
| Source Color | **Auto (Recommended)** |

Click **Prepare Source** and wait for Source Ready. Valid cached frames are reused.
For tracking, prepare the required range; **Current Frame** prepares only one frame.
**Next to Nuke Script** needs a saved .nk. **Custom Folder** lets you choose a writable folder.
To change these later, use **Cache / Setup**; keep cache folders accessible for the shot.

## 3. Select — guide each object

Use **SAM 2.1**, choose an Object and click inside the subject with **Add Point**.
Create a second Object for a separate matte. The colored overlay helps distinguish the two subjects.
**Remove Point** adds background/exclusion guidance; it does not delete a point. Use **Undo Point** to undo an edit.

![Select — frame 1: Add Point guidance for two objects, shown in red/yellow overlay.](images/select_1.png)

*Select — frame 1: Add Point guidance for two objects, shown in red/yellow overlay.*

## 4. Track — follow the shot and correct

Set the range / In–Out and click **Track** for unfinished frames. Scrub to check the result.
At a difficult frame add correction points, set the affected In–Out and use **Update Track** to recompute existing results.
**Stop** keeps completed frames. Objects without guidance are skipped; the arrow buttons start directional tracking directly.

![Track — frame 24: two object overlays; Status shows 24 frames completed.](images/track_2.png)

*Track — frame 24: two object overlays; Status shows 24 frames completed.*

## 5. ViTMatte OFF / ON — compare the edges

Select **Matte** in View. Toggle **ViTMatte** while inspecting the same frame to compare the contour.
ViTMatte is optional edge refinement, not a tracking model, and uses additional GPU resources.
Its model is prepared by standard Full Setup. Check the result on your own shot.

| ViTMatte OFF · frame 24 | ViTMatte ON · frame 24 |
| --- | --- |
| <img src="images/vitmatte_off_3.png" alt="ViTMatte OFF — frame 24, Matte View." width="460"> | <img src="images/vitmatte_on_3.png" alt="ViTMatte ON — frame 24, Matte View; compare the displayed edges with OFF." width="460"> |

*Same displayed frame in Matte View: compare the edges. This example is not a guarantee for every shot.*

For small matte changes use **Adjustment**: Fill Holes, Remove Specks, Grow / Shrink, Feather and Close Gaps.
Global controls in Node Properties and the Editor share the same state. **Object Override** changes only the chosen object.

## 6. Cutout — inspect the current-frame result

Choose **Cutout** in View to see the subjects against black using the current matte.
This preview is useful before output; it does not mean every frame is ready for rendering.

![Cutout — frame 24 current-frame preview. Final mattes are paused at 9/24; this is not a completed Write.](images/complete_4.png)

*Cutout — frame 24 current-frame preview. Final mattes are paused at 9/24; this is not a completed Write.*

User-provided operation examples captured in a development checkout displaying v1.0.0 (build 2f574ca). These are not native acceptance evidence for the published v1.0.0 ZIP (a2545b9) or v1.1.0. The Cutout shows the current frame, not all Final Mattes or a completed Write.

## 7. Use alpha and render with Write

Connect the SAM Roto Group to a Nuke Viewer and inspect **rgba.alpha** with **A**.
RGB stays the Source; alpha combines enabled objects. For a separate object output use
**Node Properties → Output → Object Matte → Create Object Matte**.

Connect **Write** and render in the Nuke GUI. Required Final Mattes prepare with progress,
then the original Render continues automatically. Cancel also cancels the waiting render.
**Output Options → Precompute Final Mattes** is optional, not a routine prerequisite.

**[Download Latest Installer](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/latest/download/SAM-Roto-for-Nuke-INSTALLER.zip)** · [日本語ガイド](QUICKSTART_JA.md)

## Update, recover and get help

- Updater-enabled Public installs check Stable updates after opening the SAM Window, at most once per 24 hours.
  **Support → Check for Updates** also checks manually. When an update is available, use **Update** to
  download/verify, save your work, then **Install & Restart Nuke**. Finish Source preparation, Track and Render first.
  Downloading does not replace running code. Cancelling Save or Nuke exit prevents installation.
- Older versions without the updater, or incompatible runtime/models, require the Installer above.
  Save work, close all Nuke sessions, then use installer **Update / Repair**. It gracefully stops only a
  proven owned leftover backend; unknown listeners/processes block the update and unrelated processes are untouched.
  Compatible runtime/models and artist cache, points, tracking and state are retained; do not uninstall first.
- Incomplete components: use the same installer's **Repair**. Do not delete valid caches to fix setup.
- CUDA/backend error: use **Support → Logs / Copy Diagnostics**. Review screenshots/logs for private information before sending.
- Development checkouts keep **DEV Sync + Reload**. Do not install Public over your normal DEV profile.

Windows SAM 3 / 3.1 is unavailable; Linux is experimental and requires installer Advanced plus approved HF access.
Farm / Nuke -t / -x does not perform automatic inference or Final preparation: deliver prepared caches/runtime
or bake to standard nodes. Get Color and Ctrl+Shift+C custom hotkey are not included.

[Detailed installation / recovery](INSTALLATION.md) · [Release notes](RELEASE_NOTES_1.1.0_EN.md) ·
[Screenshot captions / reuse](SCREENSHOTS.md) · [Licenses / notices](../THIRD_PARTY_NOTICES.md)
