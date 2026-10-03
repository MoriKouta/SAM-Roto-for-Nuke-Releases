# Install and make your first matte

[日本語](QUICKSTART_JA.md) · [Download v1.0.0](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/tag/v1.0.0)

**Download → Full Setup → Open → Prepare Source → Point → Track / correct → ViTMatte → alpha / Write**

Windows / Linux x86_64 and an **NVIDIA CUDA-capable GPU** are required. Nuke 15.2 / 16.0 / 16.1 / 17.x
are compatibility targets; validation is not complete for every OS/Nuke/GPU combination.
macOS and CPU-only / AMD-only / Intel-only inference are not supported in v1.0.0.
Internet is needed for installation/repair. Allow 20 GB free for standard setup, plus shot caches.

## 1. Download and run Full Setup

1. Download **[SAM-Roto-for-Nuke-v1.0.0.zip](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/download/v1.0.0/SAM-Roto-for-Nuke-v1.0.0.zip)** and extract it.
2. Save your work, close Nuke and stop the SAM Roto backend before installing. Open the extracted folder.
3. Windows: run **install_windows.bat**. Linux: run **install_linux.sh**.
4. Click **Install SAM Roto**. Wait for **SAM Roto is ready**, then click **Finish**.

No system Python, Git, pip commands or startup editing. Full Setup downloads Python/PyTorch,
SAM 2 / 2.1 Base+ and ViTMatte models; uv and SAM source archives are already in the ZIP.
Point, Track and ViTMatte use the prepared models locally. Keep the installer for Repair/update.
Linux uses an available desktop UI or a terminal fallback; enable file execution in Properties if needed.

| Install | Finish |
| --- | --- |
| <img src="images/install-v1.0.0.png" alt="v1.0.0 installer with Install SAM Roto button" width="340"> | <img src="images/finish-v1.0.0.png" alt="v1.0.0 Full Setup completion with Finish button" width="340"> |

*Actual Windows v1.0.0 installer and Full Setup completion captures.*

## 2. Open SAM Roto and prepare the Source

Restart Nuke. Select the image/source node and choose **SAM Roto → Open SAM Roto**.
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

## 3. Add guidance points

Use the default **SAM 2.1** model. Choose an Object, select **Add Point**, then click inside the subject.
**Remove Point** adds background/exclusion guidance; it does not delete an existing point.
Use **Undo Point** to undo a point edit. Create another Object for a separate matte.

*Editor images below are actual Windows window captures from a **private 1.0.1 update-test fixture**,
displaying saved synthetic source/matte pixels. They illustrate control locations, are not formal
v1.0.0 screenshots, and do not demonstrate a new inference, Track, Write or quality comparison.*

![Point controls and saved synthetic matte — private 1.0.1 fixture](images/point.png)

*Point controls with a saved synthetic matte — private 1.0.1 fixture.*

## 4. Track, inspect and correct

Set the tracking range / In–Out, then click **Track** to fill unfinished frames.
Scrub the result. At a difficult frame add foreground/background correction points, set In–Out for the
affected range, and click **Update Track** to recompute existing results. **Track** continues unfinished frames.
**Stop** ends the active run and keeps completed frames. Objects without guidance are skipped.
The arrow buttons below Track start directional tracking directly.

![Timeline at frame 5 with saved matte — private 1.0.1 fixture](images/track.png)

*Frame 5 / timeline display of saved data — private 1.0.1 fixture; no new tracking was run for this capture.*

## 5. Adjust the matte and optionally use ViTMatte

Open **Adjustment** for Global Adjustment: Fill Holes, Remove Specks, Grow / Shrink, Feather and Close Gaps.
Global controls also appear in Node Properties and share the same state. Use **Object Override** only
when one object needs different settings.

Enable **ViTMatte** for optional edge refinement and inspect the current frame. It uses additional GPU
resources and refines the matte; it is not a tracking model. Its model is included in standard Full Setup.

![ViTMatte controls with saved result — private 1.0.1 fixture](images/vitmatte.png)

*ViTMatte controls and a saved matte — private 1.0.1 fixture; not an OFF/ON comparison.*

## 6. Use alpha and render with Write

Connect the SAM Roto Group to a Nuke Viewer and inspect **rgba.alpha** with **A**.
RGB stays the Source; alpha combines enabled objects. For a separate object output use
**Node Properties → Output → Object Matte → Create Object Matte**.

Connect a **Write** and render normally in the Nuke GUI. Required Final Mattes prepare with progress,
then the original Render continues automatically. Cancel also cancels the waiting render.
**Output Options → Precompute Final Mattes** is optional; it is not a routine prerequisite.

![Matte view and Output Options — private 1.0.1 fixture](images/alpha.png)

*Saved matte view and Output Options — private 1.0.1 fixture; not a new Nuke alpha/Write validation.*

## Update, recover and get help

- Update: save work, close Nuke/backend and run the new approved installer. Compatible runtime/models
  and artist cache, points, tracking and state are retained; do not uninstall first.
- Incomplete components: use the same installer's **Repair**. Do not delete valid caches to fix setup.
- CUDA/backend error: use **Support → Logs / Copy Diagnostics**. Review screenshots/logs for private information before sending.
- Development checkouts keep **DEV Sync + Reload**. Do not install Public over your normal DEV profile.

Windows SAM 3 / 3.1 is unavailable; Linux is experimental and requires installer Advanced plus approved HF access.
Farm / Nuke -t / -x does not perform automatic inference or Final preparation: deliver prepared caches/runtime
or bake to standard nodes. Get Color and Ctrl+Shift+C custom hotkey are not included.

[Detailed installation / recovery](INSTALLATION.md) · [Release notes](RELEASE_NOTES_1.0.0_EN.md) ·
[Screenshot captions / reuse](SCREENSHOTS.md) · [Licenses / notices](../THIRD_PARTY_NOTICES.md)
