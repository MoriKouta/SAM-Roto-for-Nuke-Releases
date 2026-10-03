# Installation, updates and troubleshooting

**First time? Start with the [illustrated install / first matte guide](QUICKSTART_EN.md).**

[日本語](INSTALLATION_JA.md) · [Product guide](../README.md)

v1.0.0 is published. Use only the approved package from the
[distribution Releases](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases).
A repository source ZIP is not an installer.

## Install

1. Download the release ZIP and extract it.
2. Close Nuke and stop the SAM Roto backend; open the extracted SAM-Roto-for-Nuke folder.
3. Run install_windows.bat or install_linux.sh and choose **Install SAM Roto**.
4. Wait for **SAM Roto is ready → Finish**, restart Nuke, select a source and choose **SAM Roto → Open SAM Roto**.

Linux uses Tk or an available desktop dialog; without one it uses a terminal with the same stages.
If the ZIP extractor removed executable permission, enable “Allow executing file as program” in Properties.
Select **Run in Terminal** when the file manager offers that option.
No system Python/Git, startup edits or environment setup are required.

The destination is HOME/.nuke/SAMRoto (Windows: USERPROFILE when HOME is absent).
The displayed install path is authoritative; NUKE_PATH does not change it.
Linked/reparse installation paths are refused. Network home/UNC permissions require studio validation.

Packaged uv and SAM sources are verified offline. Python 3.12.14, torch 2.10.0+cu128,
torchvision 0.25.0+cu128 and other locked packages download during installation using system trust.
Full Setup downloads pinned SAM 2/2.1 Base+ checkpoints and the fixed-revision ViTMatte model.
It validates SHA-256 and local-only CPU model loading before registration. Subsequent Point/Track/
ViTMatte operations require no model network access. Missing/corrupt models are an incomplete install:
re-run this installer and choose **Repair**. No cache deletion or manual package setup is necessary.
SAM 3 is excluded from standard setup. Linux **Advanced** can prepare experimental SAM 3/3.1
with explicitly entered, approved HF access; Windows entries are unavailable. Tokens are never logged.
Adding this optional runtime later uses a journaled rebuild rather than changing a working venv in place;
failure/Cancel restores that runtime. Ordinary compatible updates still reuse it without rebuilding.
**Windows / Linux x86_64: Supported. macOS: Not supported in v1.0.0.**
No additional render license is used by Source preparation.

Allow 20 GB free for standard setup, or 40 GB with optional SAM 3, plus shot caches.
The published v1.0.0 installer ZIP is 39,337,331 bytes; see the Release for its checksum.
No universal shot cache size or VRAM requirement is claimed.

## Update

Close Nuke/backend and run the new release's same installer. Do not uninstall first.
The installer validates application bytes and updates only managed code in a compatible healthy install.
Healthy runtime/models are reused without downloads. **Repair** restores missing models or rebuilds a
broken installer-owned runtime with rollback; healthy model bytes and artist data remain.
Python, PyTorch, SAM sources, models/checkpoints, caches, points, tracking, settings and .nk files remain.
It reports **updated successfully** and **Runtime/models preserved**.
If runtime compatibility changes in a future release, explicit setup is required; a normal code update
does not silently rebuild the environment.

Unrelated init.py/menu.py bytes, encoding and line endings are retained. Only installer-owned
registration blocks change; no new registration is added to root menu.py.

## Uninstall

Close Nuke and run **uninstall_windows.bat** or **uninstall_linux.sh** from the extracted package.
This uses the existing managed Python, makes no downloads and removes only SAM Roto startup registration.
Restart Nuke. Runtime, models, application files and artist caches remain for reuse.

Advanced **application removal** also removes manifest-owned code, with rollback:
Windows: run the package's `scripts/uninstall_windows.ps1 -Application` in PowerShell;
Linux: `./uninstall_linux.sh --application`.
Use the extracted package, not a deleted installed copy.
Models/runtime/unlisted artist files remain. There is no one-click full purge: shared Hugging Face
stores and shot caches may belong to other tools/projects. Select such data only after an explicit
ownership/backup review with support. Never delete .nuke as an uninstall operation.

## Troubleshooting

| Symptom | What to check |
|---|---|
| No SAM Roto menu | Restart the Nuke GUI. Compare the displayed install location to Nuke's HOME policy. Check Script Editor startup errors. Batch sessions intentionally have no menu. |
| Installed, but CUDA GPU is unavailable | Installation succeeded, inference did not. Check NVIDIA CUDA GPU/driver. CPU/AMD-only/Intel-only are unsupported. |
| Preparing Python / installing dependencies failed | Check available storage, network/proxy and OS certificate trust. Never disable TLS or use trusted-host. Send the safe installer log. |
| Model preparation failed / incomplete installation | Check Internet, proxy/certificate trust and disk space; re-run installer Repair. Nuke does not download missing models. Keep caches. |
| SAM 3 access denied | Linux experimental only: request approved model access and use installer Advanced. Do not send tokens in reports. Windows entries are unavailable. |
| Cache unavailable | In Setup choose a writable Cache Location; Next to Nuke Script requires a saved .nk. Prepare missing frames; do not clear valid caches. |
| Final preparation failed | Read the specific failure/cancel status, confirm the required Source/Raw cache remains accessible and retry after resolving it. Manual Precompute is an advanced option, not a routine prerequisite. |
| Update says backend running | Finish work, close the Editor/Nuke and stop the backend using its normal controls. Do not kill unrelated processes. |
| Linked path refused | Use a regular directory; symlink/reparse destinations are intentionally unsupported. |
| Startup markers malformed | Preserve the startup file. Ask support to inspect the owned marker boundaries; installer does not guess or delete unrelated code. |

## Interrupted installation / recovery

Ordinary failures roll back transaction-owned application/startup changes. Existing working installs
are preserved. A forced exit/power loss leaves a recovery lock/journal. Do not delete locks, backup
folders or an incomplete target based only on its presence.

Close Nuke/backend and send the log to the maintainer. The existing `install.py --recover` operation
uses the package's managed Python to recover only an identified transaction.
Support must identify whether this is a fresh migration, update or uninstall journal before proceeding.
A legacy Sammie install follows the installer migration transaction; do not move editable environments manually.
For a recognized interrupted install/update, the same installer offers **Repair** and restores its own
journal before retrying. Cancel remains active while downloads/commands run and waits for owned-process
shutdown and rollback. Unknown/malformed journals fail closed; no unrelated directory is deleted.

## Logs and reports

The resolved Nuke user directory contains **.samroto-bootstrap/install.log**.
It records timestamp, application version, stage, platform and sanitized result/error.
It deliberately excludes raw child output, tokens, private paths and production node names.
Use **Support → Copy Diagnostics** for version/build/channel, OS/Nuke/Python, model,
observed backend/GPU/CUDA/cache state and safe error category. Unobserved backend fields are unknown.

Send: reproduction steps, expected/actual result, Nuke version/OS and diagnostics.
Review screenshots and manually attached logs for confidential details first.

## Advanced integrity verification

The .zip.sha256 sidecar is optional for manual download verification; it is not a normal install step.
Internal application manifest, uv checksum, source revision/hash, traversal and symlink checks always run.
Keep the package from a trusted Release: an embedded hash detects mismatches but is not a publisher signature.

## Native acceptance

Repeat on each available **Nuke 15.2, 16.0, 16.1 and 17.x**, Windows and Linux:

1. Install in a fresh test profile with an unrelated plugin; confirm all Full Setup stages and Finish.
   Disconnect Internet **before restarting Nuke**; confirm menu/version/build.
2. Prepare a short Source; check narrow/HiDPI Setup and each Cache Location.
3. SAM 2.1: Add/Remove Point, Undo Point, multiple objects including one unguided, Track/Stop.
4. Correct a frame; **Update Track** recomputes existing In/Out results; **Track** fills unfinished results.
5. Global Adjustment/Object Override, **first ViTMatte enable offline**, combined/object alpha,
   one-click Write and Cancel. Confirm no model download/setup prompt and correct alpha.
6. Save/Open .nk; reopen/minimize/maximize; update a previous install and confirm cache/state/model reuse.

Automated tests and historical development runs do not replace this v1.0.0 checklist.
Repeat installer Cancel/Retry and a compatible application update; verify no healthy runtime/models
are downloaded again. Linux optional SAM 3/3.1 requires separate gated-access/native acceptance.
