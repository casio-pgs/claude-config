---
name: YouTube自動アップロード設定
description: コマンド一発でYouTubeに非公開アップロードできる環境が整っている
type: project
originSessionId: c3a6aa47-8a7a-4e3b-b004-917ef9b93276
---
スクリプトとOAuth認証済みトークンを設置済み。非公開アップロードがコマンド一発で動く。

**スクリプト：** `/Users/casio/tools/youtube_upload.py`
**認証情報：** `/Users/casio/tools/youtube_client_secret.json`（Google Cloud: kasioWebプロジェクト）
**トークン：** `/Users/casio/tools/youtube_token.json`（初回認証済み、2回目以降ブラウザ不要）

使い方：
```bash
python3 ~/tools/youtube_upload.py "動画ファイル.mov"
python3 ~/tools/youtube_upload.py "動画ファイル.mov" --title "タイトル" --public
```

**Why:** 生徒向け説明動画をYouTubeに手軽に上げるため
**How to apply:** 動画アップロードの話が出たらこのスクリプトを案内する
