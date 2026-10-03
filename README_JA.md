# SAM Roto for Nuke v1.0.0

Nuke内のポイント指定AIロト。ObjectごとのMatteをTrack／修正し、Adjustment／任意のViTMatteで
edgeを調整して、そのままNuke alpha／Writeへ出力します。

**[v1.0.0ダウンロード](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases/download/v1.0.0/SAM-Roto-for-Nuke-v1.0.0.zip)** · **[インストール／使用ガイド](docs/QUICKSTART_JA.md)** ·
**[English guide](docs/QUICKSTART_EN.md)**

## 最初の手順

1. ZIPを取得して展開。
2. 作業を保存してNuke／backendを終了。**install_windows.bat／install_linux.sh** を実行。
3. **Install SAM Roto → Full Setup → Finish**。Nuke再起動。
4. Source選択 → **SAM Roto → Open SAM Roto → Prepare Source**。
5. **Add Point → Track → 修正Point／Update Track**。
6. 任意の **ViTMatte** → **rgba.alpha** を確認 → **Write** を接続してRender。

system Python／Git／startup編集は不要です。標準Full SetupでSAM2／2.1 Base+とViTMatteのモデルを準備し、
以後はlocalで使います。更新は互換runtime／モデルとArtistデータを保持します。

![v1.0.0 Full Setup完了の実際の画面](docs/images/finish-v1.0.0.png)

*Windows v1.0.0 installer：Finish後にNukeを再起動。*

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

installer画像はv1.0.0です。ガイドのEditor画像は **private 1.0.1更新テストfixture** で保存済みsynthetic
Matteを表示したものです。正式v1.0.0の画面や撮影時の新規推論／Write検証とは扱いません。

## 整合性・ライセンス

ZIP SHA-256: `12d9f0d090937cffc9b17a6f170c686b607283607d8d1ba5bab579dd59ab02fb`
Application commit: `a2545b988bc86b57dffc145c9f9bcad87508c663` · 39,337,331 bytes。
手動checksum比較は任意です。内部application／uv／source検証は維持します。
ZIP内の一部文書に準備時のDraft表記が残っていますが、この公開Releaseで配布物を識別してください。
本体オリジナルコードはMIT、第三者componentは各々の条件に従います。
[LICENSE](LICENSE) · [第三者通知](THIRD_PARTY_NOTICES.md) · [固定依存一覧](docs/THIRD_PARTY_INVENTORY.md)
