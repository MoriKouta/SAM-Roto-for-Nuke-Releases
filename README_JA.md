# SAM Roto for Nuke v1.0.0

Nuke内で使うPoint指定のAIロト。複数対象を指定してTrack／修正し、任意のViTMatteで輪郭を調整。
MatteをそのままNuke alpha／Writeへ出力します。

## 短い導入

ZIPを取得・展開 → 作業保存・Nuke／backend終了 → **install_windows.bat／install_linux.sh**
→ **Install SAM Roto → 自動Full Setup → Finish** → Nuke再起動。
Source選択 → **SAM Roto → Open SAM Roto → Prepare Source**。
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

操作画像は、v1.0.0表示の開発checkout（build 2f574ca）で撮影したユーザー提供例です。公開ZIP（a2545b9）のnative acceptance証拠ではありません。Cutoutはcurrent frameのpreviewで、全Final MatteやWriteの完了を示しません。

## ダウンロード／ガイド

**[v1.0.0ダウンロード](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/download/v1.0.0/SAM-Roto-for-Nuke-v1.0.0.zip)** · **[日本語インストール／使用ガイド](docs/QUICKSTART_JA.md)** ·
**[English guide](docs/QUICKSTART_EN.md)**

Full SetupでPython／PyTorch、SAM2／2.1 Base+とViTMatteのモデルを準備し、以後はlocalで使います。
更新は互換runtime／モデルとArtistデータを保持。ガイドには実v1.0.0のInstall／Finish画面も掲載しています。

## 必要条件・制限

- **Windows／Linux x86_64、NVIDIA CUDA GPU必須**。install／RepairにはInternetが必要です。
- 標準setup中は20 GBの空き＋shot cache容量を確保。GPUメモリはshotにより変わります。
- Nuke 15.2／16.0／16.1／17.xが互換対象です。全OS／Nuke／GPUの組み合わせで検証完了しているわけではありません。
- v1.0.0はmacOS／CPUのみ／AMDのみ／Intelのみの推論に非対応。
- Windows SAM3／3.1は利用不可。LinuxはExperimentalでinstaller Advancedと承認済みHF accessが必要です。
- Farm／terminalは準備済みCache／runtimeか標準nodeへのベイクが必要です。自動推論は行いません。
- Get Color、Ctrl+Shift+C custom hotkeyは未搭載です。

CUDA／backendの問題は **Support → Logs / Copy Diagnostics**。報告されたSAM2.1 Add Pointの
CUDA unknown errorの物理原因は未特定です。添付前に画像／logの機密情報も確認してください。
**Support → Check for Updates** は手動確認で、自動installはしません。
開発checkoutは **DEV Sync + Reload** を継続します。通常DEV profileへ公開版を上書きしないでください。

## ガイド・画像

[日本語](docs/QUICKSTART_JA.md) · [English](docs/QUICKSTART_EN.md) ·
[詳細install／復旧](docs/INSTALLATION_JA.md) · [Release notes](docs/RELEASE_NOTES_1.0.0_JA.md) ·
[画像URL／キャプション](docs/SCREENSHOTS.md)

ガイドには実際のv1.0.0 installer画面も保持しています。

## 整合性・ライセンス

ZIP SHA-256: `12d9f0d090937cffc9b17a6f170c686b607283607d8d1ba5bab579dd59ab02fb`
Application commit: `a2545b988bc86b57dffc145c9f9bcad87508c663` · 39,337,331 bytes。
手動checksum比較は任意です。内部application／uv／source検証は維持します。
ZIP内の一部文書に準備時のDraft表記が残っていますが、この公開Releaseで配布物を識別してください。
本体オリジナルコードはMIT、第三者componentは各々の条件に従います。
[LICENSE](LICENSE) · [第三者通知](THIRD_PARTY_NOTICES.md) · [固定依存一覧](docs/THIRD_PARTY_INVENTORY.md)
