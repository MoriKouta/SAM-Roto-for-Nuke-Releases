# SAM Roto for Nuke v1.0.0

**v1.0.0公開版です。** 本体のオリジナルコードはMIT、第三者componentは各々の条件に従います。
Windows/Linux対応と実機検証の未完了記録は、公開判断から分けて表示します。
管理者のv1.0.0公開方針では、両OSの実機検証完了を公開必須条件にはしていません。

[English](RELEASE_NOTES_1.0.0_EN.md)

Nuke内のポイント指定AIロト。複数Object、Track／修正、Global Adjustment、
Object Override、任意のViTMatte、rgba.alpha／Write出力をまとめて扱います。

## インストール／更新

Windows／Linux x86_64、**NVIDIA CUDA GPU必須**。
SAM-Roto-for-Nuke-v1.0.0.zipを取得・展開し、Nuke／backendを終了、
install_windows.bat／install_linux.sh → Install SAM Roto → 自動Full Setup → Finish。Nukeを再起動し
SAM Roto → Open SAM Rotoを開いてください。
system Python／Git／startup手編集は不要です。更新時は互換runtime／モデル／Artistデータを保持します。
Python／PyTorch、SAM2／2.1 Base+、ViTMatteをinstall中に取得し、固定SHA・local-only loadまで検証します。
Point／Track／ViTMatteの初回操作で追加downloadはありません。不足componentは同じinstallerのRepairで修復します。
Cancel／RetryはArtistデータを保持し、Windows native UIとLinux desktop／terminalは同じtransactionを使います。
macOSはv1.0.0では非対応です。
[インストールと復旧](INSTALLATION_JA.md)を参照してください。

## 既知の制限

- Nuke 15.2／16.0／16.1／17.xのv1.0.0実機受入は未完了です。
- Windows SAM3／3.1は無効化。Linux Experimentalはinstaller Advancedで承認済みHF accessとともに事前準備します。
- CPU／AMDのみ／Intelのみ／macOSの推論は非対応です。
- Get Color、Ctrl+Shift+C custom hotkeyは未搭載です。
- Farm／terminalは準備済みCache／runtimeか標準nodeへのベイクが必要で、自動推論は行いません。
- 品質・GPUメモリ・速度はshotに依存し、ViTMatteは追加GPU負荷があります。

Support → Logs / Copy Diagnosticsと短い再現手順で報告してください。
Supportから公開Stableの更新確認ができます。自動更新は行いません。
install logは.nuke/.samroto-bootstrap/install.logです。添付資料の機密情報も確認してください。

SAM2.1 Add Pointで報告されたCUDA unknown errorの物理原因は未特定です。
