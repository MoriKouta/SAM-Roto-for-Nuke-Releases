# SAM Roto for Nuke v1.1.0

**In-App Updater, including the v1.0.4 installer and download fixes.**

Public installations check for Stable updates shortly after opening the SAM Window, at most once per
24 hours. Support shows a small version notice. **Update → Download/Verify → Install & Restart Nuke**
prepares a verified package without changing the running application. Save your script before restart.
An external runner waits for the initiating Nuke to exit, refuses other active Nuke hosts, and uses
v1.0.4's canonical backend ownership/graceful shutdown and existing code-only transaction/rollback.
No unknown process is killed. Runtime, models, cache, Points, Tracking, Matte and .nk data are retained.
Runtime/model policy changes require the release installer. Unknown restart arguments require manual restart.

The installer also uses the same verified backend shutdown after Nuke closes. Source monitoring retains
the performance follow-up: Properties presentation does not invalidate Source identity, and healthy
targeted watches use bounded metadata probes. Final/Write freshness remains enforced.

DEV keeps Sync + Reload. Internal RC does not automatically check Stable. No global graph callbacks
or Nuke-startup network checks are added. Public assets use SAM-Roto-for-Nuke-INSTALLER.zip and its
checksum; historical <=1.0.3 versioned assets remain readable and unchanged.

Windows/Linux x86_64 are the targets. Native Nuke end-to-end update/restart acceptance is pending.
Nuke-free regression and distribution checks establish internal behavior only, not native acceptance.
The maintainer approved v1.1.0 publication after internal verification. Older releases/tags/assets remain unchanged.
