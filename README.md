# hackCraft2-editor

hackCraft2 プラグイン（minigame モード）が起動時に取得する **Web エディタ配信物** のホスト。

- **手動編集しないこと。** 中身は `0x48lab/hackCraft2` の `www/public` ビルド成果物から生成される。
- 配信フロー:
  1. `main` の `manifest.json` … 現在バージョン・tar.gz の URL・sha256・サイズを記載（プラグインが最初に取得する軽量エンドポイント）
  2. Release `web-<version>` … `hackcraft2-web.tar.gz`（本体。エディタ SPA 群＋3D テクスチャ）

## 収録物

`minigame-editor / code / scratch / 3dview / dcraft / assets / js / images`
（learning 専用の `direct_method / doc / python / items` は除外）

## プラグイン側の取得手順

1. `manifest.json` を取得し、ローカルの `.version` と比較
2. 差分があれば `url` の tar.gz をダウンロード
3. `sha256` を検証
4. `plugins/hackCraft2/www/` へアトミックに展開

> 将来的に `0x48lab/hackCraft2` の CI が push 契機で自動更新する予定（現時点は手動公開）。
