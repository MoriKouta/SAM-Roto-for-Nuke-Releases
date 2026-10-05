# SAM Roto for Nuke v1.0.3

## 変更点

- 大規模compの通常操作を停止させていた、SAM Rotoの全ノードgraph callbackを撤去しました。
  無関係なknob変更・選択・移動・接続でSource hash、graph探索、idle Final失効、Cancelを行いません。
- 各SAM Sourceの依存だけを監視します。実際のpixel変更やSAM入力変更では対象Outputを失効させ、
  Write開始前にもSourceを検証します。Artist state、Source JPEG、Raw、Tracking、Matte／Cache形式は維持します。
- idle準備、foreground優先、Cancel、node削除／DEV Reloadの所有権を維持しました。
- v1.0.2候補のLinux HOME alias、CRLF metadata、旧startup移行、Repair修正も含みます。

## インストール／更新

1. [最新Release](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/latest)からZIPを取得します。
2. 展開して`SAM-Roto-for-Nuke`を開き、作業を保存してNukeとSAM Roto backendを終了します。
3. **install_windows.bat** または **./install_linux.sh** → **Install SAM Roto／Update／Repair**。
4. **SAM Roto is ready → Finish** まで待ち、Nuke再起動 → **SAM Roto → Open SAM Roto**。

事前アンインストールは不要です。互換性のある正常runtime／modelsとArtist cacheを再利用します。
Full Setup／RepairにはInternetが必要です。system Python／Git、startup手編集は不要です。
Windows／Linux x86_64とNVIDIA CUDA対応GPUが必要です。macOS、CPUのみ／AMDのみ／Intelのみの推論は非対応です。
SAM3／3.1は承認済みHF accessを使うLinuxの実験的機能で、Windowsでは利用できません。

## 検証範囲／制限

Nukeを使わない自動testでcallback回数、Source identity、寿命管理、Cache、Writeを確認しています。
旧callback解除でLinux／Nuke 15.2v4の操作性が戻ったことはArtist報告に基づきます。
今回buildのWindows／Linux GUI／GPU実機受入は未完了です。大規模compの応答性、実Source変更、idle Final、
Write／Cancel、Editor再Open、DEV SyncをNuke 15.2／16／17で確認してください。
Linux Fresh Installと旧環境Repairも、HOME上書き・迂回コマンドなしでの実機確認が必要です。

問題があればVersion／Build、OS／Nuke、再現手順と **Support → Copy Diagnostics** を報告してください。
私的script、業務素材、token、個人pathは送らないでください。既存公開ZIP／tagは変更しません。
[LICENSE](../LICENSE)、[第三者通知](../THIRD_PARTY_NOTICES.md)、[依存一覧](THIRD_PARTY_INVENTORY.md)を維持します。

[English](RELEASE_NOTES_1.0.3_EN.md) · [インストール](INSTALLATION_JA.md) · [使い方](../README_JA.md)
