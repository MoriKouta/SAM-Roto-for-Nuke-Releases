# SAM Roto for Nuke v1.1.0

Nuke内で使うPoint指定のAIロト。複数対象を指定してTrack／修正し、任意のViTMatteで輪郭を調整。
MatteをそのままNuke alpha／Writeへ出力します。

## 短い導入

ZIPを取得・展開 → 作業保存・Nuke終了 → **install_windows.bat／install_linux.sh**
→ **Install SAM Roto → 自動Full Setup → Finish** → Nuke再起動。
Node GraphでSourceを選択 → **Tab →「SAM Roto」と検索 → SAM Roto**。
接続済みGroupが作成されPropertiesが開きます → **Open Editor → Prepare Source**。
Source未選択時は案内だけを表示し、nodeを作成しません。
上部の **SAM Roto → Open SAM Roto** メニューも引き続き使えます。
最初は **Full Range／Local Cache／Auto**。system Python／Git／startup編集は不要です。

## Select

Objectを選び、**Add Point** で対象を指定。別対象には別Objectを作ります。

![Select — frame 1。Add Pointで2対象を指定し、赤／黄のoverlayで確認。](docs/images/select_1.png)

*Select — frame 1。Add Pointで2対象を指定し、赤／黄のoverlayで確認。*

## Track

**Track** で未完了frameを進めます。scrubして修正Pointを追加し、**Update Track** で既存結果を再計算。

![Track — frame 24。2対象のoverlayと、Statusの24 frames completed表示。](docs/images/track_2.png)

*Track — frame 24。2対象のoverlayと、Statusの24 frames completed表示。*

## ViTMatte OFF／ON

同じframeの **Matte View** で任意の **ViTMatte** を切り替え、輪郭を比較します。

| ViTMatte OFF · frame 24 | ViTMatte ON · frame 24 |
| --- | --- |
| <img src="docs/images/vitmatte_off_3.png" alt="ViTMatte OFF — frame 24, Matte View." width="460"> | <img src="docs/images/vitmatte_on_3.png" alt="ViTMatte ON — frame 24, Matte View; compare the displayed edges with OFF." width="460"> |

*同じframeのMatte Viewで輪郭を比較できます。すべてのshotで同じ効果を保証するものではありません。*

## Cutout／出力

**Cutout View** でcurrent frameの切り抜きを確認。Nukeの **rgba.alpha** を確認して **Write** を接続します。
GUI Render時は必要なFinal Matteを準備してから元のRenderを自動続行します。

![Cutout — frame 24のcurrent-frame preview。Final mattesは9/24でpaused。Write完了画像ではありません。](docs/images/complete_4.png)

*Cutout — frame 24のcurrent-frame preview。Final mattesは9/24でpaused。Write完了画像ではありません。*

操作画像は、v1.0.0表示の開発checkout（build 2f574ca）で撮影したユーザー提供例です。公開v1.0.0 ZIP（a2545b9）のnative acceptance証拠ではありません。Cutoutはcurrent frameのpreviewで、全Final MatteやWriteの完了を示しません。

## ダウンロード／ガイド

**[最新版Installerをダウンロード](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/latest/download/SAM-Roto-for-Nuke-INSTALLER.zip)** · **[日本語インストール／使用ガイド](docs/QUICKSTART_JA.md)** ·
**[English guide](docs/QUICKSTART_EN.md)**

**SAM-Roto-for-Nuke-INSTALLER.zip** を取得してください。現在の公開版は **[v1.1.0](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/tag/v1.1.0)** です。
[版番号付きv1.1.0 ZIP](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/download/v1.1.0/SAM-Roto-for-Nuke-v1.1.0.zip)も同じInstaller bytesです。
GitHubのSource codeはInstallerではありません。小容量Nukepedia helperは正式downloadをbrowserで開くだけです。
v1.1.0はcallback性能修正、v1.0.4の安全なbackend終了、In-App Updaterを含みます。
Nuke終了後、installerが所有を証明できる残存backendを正常終了します。不明なlistenerがあれば安全に停止します。
実Source変更は対象Outputを失効させ、Write前にSourceを再検証します。v1.0.2候補のLinux installer／旧環境Repair修正も含みます。
今回buildのGUI／GPU・大規模comp応答性・Linux Fresh Install／Repair・updaterの終了／再起動／データ保持は実機未検証です。

Full SetupでPython／PyTorch、SAM2／2.1 Base+とViTMatteのモデルを準備し、以後はlocalで使います。
更新は互換runtime／モデルとArtistデータを保持。ガイドには実v1.0.0のInstall／Finish画面も掲載しています。

## 必要条件・制限

- **Windows／Linux x86_64、NVIDIA CUDA GPU必須**。install／RepairにはInternetが必要です。
- 標準setup中は20 GBの空き＋shot cache容量を確保。GPUメモリはshotにより変わります。
- Nuke 15.2／16.0／16.1／17.xが互換対象です。全OS／Nuke／GPUの組み合わせで検証完了しているわけではありません。
- v1.1.0はmacOS／CPUのみ／AMDのみ／Intelのみの推論に非対応。
- Windows SAM3／3.1は利用不可。LinuxはExperimentalでinstaller Advancedと承認済みHF accessが必要です。
- Farm／terminalは準備済みCache／runtimeか標準nodeへのベイクが必要です。自動推論は行いません。
- Get Color、Ctrl+Shift+C custom hotkeyは未搭載です。

CUDA／backendの問題は **Support → Logs / Copy Diagnostics**。報告されたSAM2.1 Add Pointの
CUDA unknown errorの物理原因は未特定です。添付前に画像／logの機密情報も確認してください。
Public installはSAM Windowを開いた後、最大24時間に1回Stable更新を確認します。
**Support → Check for Updates** でも手動確認できます。**Update → 取得・検証 → Install & Restart Nuke**
は明示操作と作業保存が必要です。準備中は稼働コードを置換しません。runtime／model非互換ならinstallerが必要です。
開発checkoutは **DEV Sync + Reload** を継続します。通常DEV profileへ公開版を上書きしないでください。

## ガイド・画像

[日本語](docs/QUICKSTART_JA.md) · [English](docs/QUICKSTART_EN.md) ·
[詳細install／復旧](docs/INSTALLATION_JA.md) · [v1.1.0 Release notes](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/tag/v1.1.0) ·
[画像URL／キャプション](docs/SCREENSHOTS.md)

ガイドには実際のv1.0.0 installer画面も保持しています。

## 整合性・ライセンス

ZIP SHA-256: `b09b67fbe34763e66b1fb5c895b6b70c36a5fc8bda862f54d23fe51b6d597a1a`
Application source: `d12e9a4e247154fac051ab86c0510afd0ce2b58f` · 39,397,225 bytes（v1.1.0 Installer ZIP）。
手動checksum比較は任意です。内部application／uv／source検証は維持します。
本体オリジナルコードはMIT、第三者componentは各々の条件に従います。
[LICENSE](LICENSE) · [第三者通知](THIRD_PARTY_NOTICES.md) · [固定依存一覧](docs/THIRD_PARTY_INVENTORY.md)
