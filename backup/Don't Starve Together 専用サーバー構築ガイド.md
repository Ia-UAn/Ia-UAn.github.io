
![下载 (1)](https://github.com/user-attachments/assets/24a92400-33b3-410c-b2c0-68caf1322831)

# Don't Starve Together 専用サーバー構築ガイド

## 必要なもの
- **クラウドサーバー**: 2コア、4GB RAM、6Mbps以上の帯域幅（例: Tencent Cloud）
- **OS**: Windows Server 2012（他のWindows Serverも可）

## 手順

### 1. クラウドサーバーの設定
1. **ポート開放**: クラウドサーバーのコントロールパネルで全ポートを開放
2. **リモートアクセス**:
   - `Windowsキー + R`を押して`mstsc`と入力し、リモートデスクトップを開く
   - サーバーのIPアドレスと管理者パスワードを入力して接続
![OIP](https://github.com/user-attachments/assets/4bb7e75a-d4ab-446e-a456-ffb03d3512fc)

### 2. SteamCMDのインストール
1. **SteamCMDのダウンロード**: 指定のフォルダにインストール
2. **コマンドの実行**:
   ```sh
   login anonymous
   force_install_dir <インストールフォルダ>
   app_update 343050 validate
   quit

### 3. ゲームの設定
- **ローカルでゲームを起動**: ゲームを作成し、設定を保存
- **設定ファイルのコピー**: `Cluster_X`フォルダをクラウドサーバーにコピーし、`Cluster_1`にリネーム
- **サーバートークンの設定**: `cluster_token`ファイルにトークンをコピー
![OIP (1)](https://github.com/user-attachments/assets/58946058-d724-43ae-b0b1-7912eec4b670)


### 4. MODの設定（必要な場合）
- **MODファイルのコピー**: ローカルの`MOD`フォルダからクラウドサーバーの`MOD`フォルダにコピー

### 5. サーバーの起動
- **バッチファイルの編集**:
  ```batch
  start "Don't Starve Together Overworld" /D "%~dp0.." "%~dp0..\dontstarve_dedicated_server_nullrenderer.exe" -cluster Cluster_1 -console -shard Master -console
  start "Don't Starve Together Caves" /D "%~dp0.." "%~dp0..\dontstarve_dedicated_server_nullrenderer.exe" -cluster Cluster_1 -console -shard Caves -console
- バッチファイルをダブルクリック

### 6. サーバーの停止
- 停止コマンド: `c_shutdown()` を入力してサーバーを安全に停止

## 注意事項
- 手動入力を避ける: コピー＆ペーストを推奨
- ゲーム更新時の対応: サーバーのゲームバージョンを更新

