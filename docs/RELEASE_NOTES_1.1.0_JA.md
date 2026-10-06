# SAM Roto for Nuke v1.1.0

**In-App Updater。v1.0.4のinstaller・download修正を含みます。**

Public installではSAM Windowを開いた後に、最大24時間に1回Stable更新を確認します。
Supportの小さな通知から **Update → 取得・検証 → Install & Restart Nuke** と進みます。
準備中は稼働中コードを変更しません。再起動前に作業を保存してください。
外部runnerは起点Nukeの終了を確認し、他のNukeが動いていれば停止します。
v1.0.4の共通backend ownership／graceful shutdownと既存code-only transaction／rollbackを使い、
不明なprocessはkillしません。runtime／models／cache／Points／Tracking／Matte／.nkは保持します。
runtime／model仕様変更は正式installerが必要です。起動引数が不明ならNukeは手動で再起動します。

installerもNuke終了後に同じ安全なbackend終了処理を使います。Source監視の性能追加修正を保持し、
Properties表示ではSource identityを失効させず、正常な対象watchは限定的なmetadata probeを使います。
Final／Writeのfreshness検証は維持します。

DEVはSync + Reloadを維持します。Internal RCはStableを自動確認しません。
global graph callback・Nuke startupでの通信は追加しません。
正式asset名はSAM-Roto-for-Nuke-INSTALLER.zipです。旧v1.0.3以前のversion付きassetは維持します。

対象はWindows／Linux x86_64。Native Nukeの更新／再起動の通し確認は未完了です。
Nuke-free回帰・配布検査は内部動作の証拠で、実機受入の証拠ではありません。
本人は内部検査完了を条件にv1.1.0公開を承認しました。旧Release／tag／assetは変更しません。
