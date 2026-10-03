# インストール・更新・トラブル対応

[English](INSTALLATION.md) · [製品ガイド](../README_JA.md)

v1.0.0公開版の配布先です。[配布Release](https://github.com/MoriKouta/SAM-Roto-for-Nuke-Releases/releases)
で承認・公開されたpackageを使ってください。GitHubのsource ZIPはインストーラではありません。

## インストール

1. Release ZIPを取得・展開します。
2. Nuke／SAM Roto backendを終了し、展開したSAM-Roto-for-Nukeフォルダを開きます。
3. install_windows.bat または install_linux.shを実行し、**Install SAM Roto** を押します。
4. **SAM Roto is ready → Finish** のあとNukeを再起動し、Source選択 → **SAM Roto → Open SAM Roto**。

Linuxは利用できるTk／desktop dialogを使い、なければ同じ工程を表示するterminalへfallbackします。
実行権限がなければPropertiesで実行を許可し、file managerに選択肢があれば「端末で実行」を選びます。
system Python／Git、startupの手編集、環境変数設定は不要です。

配置先はHOME/.nuke/SAMRotoです。WindowsでHOMEがなければUSERPROFILEを使います。
画面に表示された実際の配置先を確認してください。NUKE_PATHでは配置先を変更しません。
symlink／reparse先は拒否します。UNC・network homeの権限はstudioで実機確認してください。

uvとSAM sourceは同梱・offline検証します。Python 3.12.14、torch 2.10.0+cu128、
torchvision 0.25.0+cu128などの固定packageはOS証明書を使って取得します。
SAM 2／2.1 Base+と固定revisionのViTMatteもinstaller内で取得します。
固定SHAとCPU local-only loadを確認してからstartupを登録し、Point／Track／ViTMatte初回操作ではdownloadしません。
不足・破損は不完全なinstallとして扱い、同じinstallerの **Repair** で直します。手動削除・package commandは不要です。
標準setupにSAM3は含みません。LinuxのAdvancedから選ぶ場合だけ、承認済みHF accessを明示入力して準備します。
tokenはlogに残しません。WindowsのSAM 3／3.1は利用不可です。
あとからoptional runtimeを追加する場合は、既存venvを直接変更せずbackup付きで構築し、失敗・Cancel時は復元します。
通常の互換code updateではruntimeを再構築しません。
**Windows / Linux x86_64: Supported。macOS: Not supported in v1.0.0。**
Source準備で追加のrender licenseは使いません。

標準setupは20 GB、SAM3選択時は40 GBの空きを確認します。shot cacheには別の容量が必要です。
旧v0.3.062-devのZIP実測は155,409,347 bytesでした。**v1.0.0のサイズではありません**。
公開後のRelease assetで実際のサイズを確認してください。Cache容量やVRAM必要量はshotで変わります。

## 更新

Nuke／backendを終了し、新Releaseの同じインストーラを実行します。事前削除は不要です。
互換性のあるready installは検証済みの管理対象コードだけを更新します。
Python／PyTorch／SAM source／モデル／Cache／Points／Tracking／設定／.nkは保持します。
完了時に **updated successfully／Runtime/models preserved** を表示します。
正常なruntime／モデルは再downloadしません。不足モデルや破損runtimeだけをRepairで補い、Artistデータは保持します。
将来runtime互換性が変わった場合は明示的なsetupが必要です。通常のcode updateで勝手に再構築しません。

無関係なinit.py／menu.pyのbytes・encoding・改行は保持します。
管理対象の登録blockだけを変更し、root menu.pyへの新規登録は行いません。

## アンインストール

Nukeを閉じ、展開したpackageの **uninstall_windows.bat／uninstall_linux.sh** を実行してください。
既存の隔離Pythonを使い、downloadせずSAM Rotoのstartup登録だけを解除します。
Nukeを再起動してください。本体・runtime・モデル・Artist Cacheは再利用のため残します。

上級者向けの**本体削除**では、rollback付きでmanifest管理下のコードも削除します。
WindowsはPowerShellでpackageの `scripts/uninstall_windows.ps1 -Application`、
Linuxは `./uninstall_linux.sh --application` を実行します。
削除するinstall先ではなく、展開したpackageを使ってください。
runtime／モデル／管理外のArtistファイルは保持します。

一括全消去は用意していません。Hugging Faceの共有model storeやshot cacheは他ツールと共有される場合があります。
削除対象とbackupをsupportと確認してから選択してください。.nuke全体は削除しないでください。

## トラブル対応

| 症状 | 確認すること |
|---|---|
| メニューがない | Nuke GUIを再起動し、配置先とNukeのHOME設定、Script Editorのstartupエラーを確認。batchではメニューを作りません。 |
| Installed, but CUDA GPU is unavailable | installは成功、推論は不可の状態です。NVIDIA CUDA GPU／driverを確認。CPU／AMDのみ／Intelのみは非対応です。 |
| Python／依存packageの取得失敗 | 空き容量・network／proxy・OS証明書を確認。TLS無効化やtrusted-hostは使わず、install logを送ってください。 |
| モデル準備失敗／不完全なinstall | network／proxy／証明書／空きを確認し、installer Repairを再実行。Nukeでは不足モデルをdownloadしません。Cacheは保持してください。 |
| SAM 3認証失敗 | Linux Experimentalのみ。access承認後installer Advancedを使用。tokenは報告に含めないでください。Windowsはloginだけでは利用できません。 |
| Cache unavailable | Setupで書き込み可能な保存先を選択。Next to Nuke Scriptは.nk保存後に利用可。不足frameを準備し、有効Cacheは保持してください。 |
| Final準備失敗 | 具体的な失敗／cancel表示とSource／Raw Cacheへのアクセスを確認。Manual Precomputeは通常操作の前提ではありません。 |
| 更新時backend running | 作業を終え、Nuke／Editorを閉じbackendを通常の操作で停止。無関係なprocessは終了しないでください。 |
| Linked path refused | 通常のdirectoryを使用。symlink／reparse先は意図的に非対応です。 |
| Startup marker不正 | startupファイルを保持してsupportへ相談。installerは推測で無関係なcodeを削除しません。 |

## 強制中断・復旧

通常の失敗は、このtransactionが変更した本体・startupだけをrollbackします。
既存のworking installは保持します。強制終了・電源断では復旧lock／journalが残ります。
存在するという理由だけでlock・backup・不完全なtargetを削除しないでください。

Nuke／backendを閉じ、logをmaintainerへ送ってください。
既存の `install.py --recover` はmanaged Pythonで特定transactionだけを復旧します。
fresh migration／update／uninstallのどのjournalかをsupportが確認してから実行してください。
旧Sammieもinstallerのmigrationを使い、editable環境を手動移動しないでください。
認識できるinstall／update中断journalは同じinstallerのRepairでrollbackしてから再試行します。
Cancelはinstaller-owned subprocess停止とrollback完了を待ちます。不正・不明なjournalはfail closedで保持します。

## logと報告

実際のNuke user directoryに **.samroto-bootstrap/install.log** を残します。
日時・version・stage・OS・sanitized結果を記録し、子processの生出力・token・private path・node名は残しません。
**Support → Copy Diagnostics** でversion/build/channel、OS/Nuke/Python、
モデル、観測済みbackend/GPU/CUDA/Cache状態、安全なエラー分類を取得できます。未観測の値はunknownです。

再現手順・期待結果と実際の結果・OS／Nuke版・diagnosticsを送ってください。
画像や手動添付logの機密情報も確認してください。

## 上級者向けchecksum確認

.zip.sha256による手動照合は任意です。通常のinstall手順には不要です。
内部manifest／uv／sourceのhash・revision、traversal・symlink検証は常に実行します。
埋め込みhashは取り違えを検出しますが発行者署名ではありません。信頼できるReleaseから取得してください。

## Nuke実機確認

利用できる **Nuke 15.2／16.0／16.1／17.x** の各Windows／Linuxで繰り返してください。

1. 無関係なpluginを置いたfresh profileへinstall。再起動しmenu／version／buildを確認。
2. 短いSourceを準備。狭い幅・HiDPI・各Cache Locationを確認。
3. SAM 2.1でAdd／Remove Point、Undo Point、複数Object（guidanceなしも含む）、Track／Stop。
4. frameを修正。**Update Track** はIn/Outの既存結果を再計算、**Track** は未完了frameを続行。
5. Global Adjustment／Object Override、任意のViTMatte、combined／object alpha、Write自動準備とCancel。
6. .nkのSave/Open、Editor復元、旧installから更新しCache／state／モデル保持を確認。

自動test・過去の開発版記録は今回のv1.0.0実機受入の代わりにはなりません。
