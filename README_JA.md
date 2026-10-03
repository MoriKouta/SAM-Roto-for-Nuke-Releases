# SAM Roto for Nuke v1.0.0

[English](README.md) · [Release／ダウンロード](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/tag/v1.0.0)

Nuke内のポイント指定AIロト。複数Object、Track／修正、Global Adjustment、Object Override、
任意のViTMatte、alpha／Write出力と自動Final準備を使用できます。

## 必要な環境

Windows／Linux x86_64、NVIDIA CUDA GPUが必要です。
macOS／CPUのみ／AMDのみ／Intelのみの推論はv1.0.0では非対応です。
Nuke 15.2／16.0／16.1／17.xは互換対象です。v1.0.0実機GUI・GPU検証は未完了のまま、公開判断と分けて記録します。

## インストール／更新

1. Releaseから **SAM-Roto-for-Nuke-v1.0.0.zip** をダウンロード。
2. 展開し、SAM-Roto-for-Nukeフォルダを開く。
3. Nuke／backendを終了し、**install_windows.bat** または **install_linux.sh** を実行。
4. Install SAM Roto → 自動Full Setup → Finish。
5. Nuke再起動 → **SAM Roto → Open SAM Roto**。

system Python／Git、環境設定やstartup手編集は不要です。Python／PyTorch、SAM2／2.1 Base+、ViTMatteを
install中に準備し、固定ハッシュ・local-only loadを確認します。標準Point／Track／ViTMatte初回操作で追加取得しません。
不足componentはRepairで修復できます。更新は互換runtime／モデル／ArtistのCache・Points・State・Trackingを保持し、
Cancel／失敗時は所有変更をrollbackします。更新時もNuke／backendを終了して同じinstallerを使用します。

通常の開発checkoutはDEV Sync + Reloadを継続使用します。開発用の通常プロファイルに公開版を上書きしないでください。
[インストール／復旧](docs/INSTALLATION_JA.md) · [Release notes](docs/RELEASE_NOTES_1.0.0_JA.md)

## 制限／サポート

- Windows SAM3／3.1は無効化。LinuxはExperimentalで、Advanced setupと承認済みHF accessが必要です。
- 実機GUI・GPU検証は未完了です。自動テストの成功を実機確認済みとは扱いません。
- SAM2.1 Add PointのCUDA unknown errorの物理原因は未特定です。診断・復旧経路は含まれます。
- Get Color、Ctrl+Shift+C custom hotkeyは未搭載。Farm／terminalは準備済みCache／runtimeか標準nodeへのベイクが必要です。
- 推論品質・速度・GPUメモリは素材とGPUに依存し、ViTMatteはGPU負荷を増やします。

Support → Check for Updatesは手動確認です。Copy Diagnosticsは機密情報を除いた報告用です。
固定ZIP内には準備時のDraft表記が一部残っています。公開状態と配布物の識別はReleaseページ／checksumで確認してください。
実機未検証値をPASSへ変更していません。

## 配布物の識別／ライセンス

Application commit: `a2545b988bc86b57dffc145c9f9bcad87508c663`
ZIP SHA-256: `12d9f0d090937cffc9b17a6f170c686b607283607d8d1ba5bab579dd59ab02fb`
手動SHA比較は任意の高度な確認です。内部uv／source／application検証は継続します。
本体オリジナルコードはMIT、第三者componentは各々の条件に従います。
[第三者通知](THIRD_PARTY_NOTICES.md) · [固定依存一覧](docs/THIRD_PARTY_INVENTORY.md)

このrepoは配布文書と承認済みRelease asset用です。開発履歴・旧Internal RCは公開配布に含めません。
