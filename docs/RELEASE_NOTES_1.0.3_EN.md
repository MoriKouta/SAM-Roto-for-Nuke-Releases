# SAM Roto for Nuke v1.0.3

## Changes

- Fix the wildcard SAM Roto graph callback that stalled ordinary comp edits in large Nuke scripts.
  Unrelated knob edits, selection, node moves and connections no longer trigger Source hashing,
  graph discovery, idle Final invalidation or cancellation.
- Watch only each SAM Source's dependencies. Actual pixel edits and SAM input changes still invalidate
  affected output; Write checks the current Source before admission. Artist state, Source JPEGs,
  Raw masks, tracking and matte/cache formats are unchanged.
- Keep idle preparation, foreground priority, cancellation and deletion/DEV Reload ownership.
- Include the v1.0.2 candidate's Linux HOME alias, CRLF metadata, legacy startup migration and Repair fixes.

## Install / update

1. Download the ZIP from the [latest Release](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/latest).
2. Extract it and open `SAM-Roto-for-Nuke`. Save work, close Nuke and stop the SAM Roto backend.
3. Run **install_windows.bat** or **./install_linux.sh**. Choose **Install SAM Roto**, **Update** or **Repair**.
4. Wait for **SAM Roto is ready → Finish**, then restart Nuke → **SAM Roto → Open SAM Roto**.

Do not uninstall first. Healthy compatible runtime/models and artist caches are reused.
Full Setup/Repair needs Internet; no system Python/Git or manual startup edits are required.
Windows/Linux x86_64 require an NVIDIA CUDA-capable GPU. macOS/CPU-only/AMD-only/Intel-only inference
is unsupported. SAM 3/3.1 remains experimental on Linux with approved HF access, unavailable on Windows.

## Validation / limitations

Nuke-free automated call-count, Source identity, lifecycle, cache and Write tests cover this fix.
The artist reported that removing the old wildcard callback restored Nuke 15.2v4/Linux responsiveness;
the new build's native GUI/GPU validation is still pending. No Windows/Linux native acceptance is
claimed. In particular, validate large-comp responsiveness, real upstream Source changes, idle Final,
Write/Cancel, Editor reopen and DEV Sync on Nuke 15.2/16/17. Linux Fresh Install and legacy Repair
must also be checked without HOME overrides or workaround commands.

For problems, report Version/Build, OS/Nuke version, steps and **Support → Copy Diagnostics**.
Do not submit private scripts, footage, tokens or paths. Existing published ZIPs/tags are unchanged.
License and third-party conditions remain in [LICENSE](../LICENSE),
[THIRD_PARTY_NOTICES](../THIRD_PARTY_NOTICES.md) and [inventory](THIRD_PARTY_INVENTORY.md).

[日本語](RELEASE_NOTES_1.0.3_JA.md) · [Installation](INSTALLATION.md) · [Usage](../README.md)
