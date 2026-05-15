---
name: サムネイル自動生成システム
description: HTML×Puppeteerでサムネを自動生成するシステムの構成・使い方・拡張内容
type: project
originSessionId: 6d9eee3b-12ed-4d13-93cf-64d31e2307d2
---
## 場所
`/Users/casio/thumbnail/`

## ファイル構成
- `template.html` — デザインテンプレート（プレースホルダー形式）
- `generate_thumbnail.js` — Node.jsで画像生成するスクリプト
- `config-example.json` — 設定ファイルのサンプル
- `ai-quest-config.json` — AI QUESTサムネ（写真なし版）
- `ai-quest-photo-config.json` — AI QUESTサムネ（写真入り版）
- `ai-quest-hero-config.json` — AI QUESTサムネ（ドット絵勇者版）

## 使い方
```bash
cd /Users/casio/thumbnail
node generate_thumbnail.js <設定ファイル>.json
```

## config.jsonの主要パラメータ
```json
{
  "BADGE_ICON": "⚔️",
  "BADGE_TEXT": "AI QUEST",
  "MAIN_TITLE": "メインタイトル",
  "SUB_LABEL": "ラベル",
  "SUB_TEXT": "サブテキスト",
  "NUM1": "項目1", "NUM2": "項目2", "NUM3": "項目3",
  "OUTPUT_FILE": "output.png",
  "BG_COLOR": "#0a0f1e",
  "BG_GRADIENT": "#0d1f0a",
  "GLOW1_COLOR": "#00aa44",
  "ACCENT_COLOR": "#00ff88",
  "ACCENT_DARK": "#00cc66",
  "ACCENT_RGBA": "0, 255, 136",
  "ACCENT_SHADOW": "0, 255, 136"
}
```

## 写真・キャラクターの追加（2026-05-10実装）

### 自分の写真を入れる場合
```json
{
  "PHOTO_PATH": "/Users/casio/Pictures/1.library/images/MNY9NILDTOZDL.info/写真の説明はありません。.jpg"
}
```
→ 右側に円形（300px）で写真が表示される。テキストは左寄せに自動調整。

### ドット絵勇者を入れる場合
```json
{
  "CHAR_TYPE": "hero"
}
```
→ 金兜・青鎧・10×18ドット絵の勇者が右円内に表示される。

### 何も指定しない場合
→ **下部に NUM1/NUM2/NUM3 の番号リストが横並びで表示される**（2026-05-16以降の標準レイアウト）。

## WP投稿との連携
`obsidian_to_wp.py` を直接呼び出してWP投稿可能。
外部画像を使う場合はmonkeyパッチで `generate_thumbnail` を差し替える：
```python
import obsidian_to_wp as wp
wp.generate_thumbnail = lambda *a, **k: "/Users/casio/thumbnail/任意の画像.png"
wp.post_to_wordpress("Obsidianファイルのパス")
```

## 注意
- X（Twitter）への自動投稿: `cd ~/tools && source venv/bin/activate && python3 x_post.py "テキスト"`（運用中）
- Puppeteer初回起動に5〜6分かかる
- サムネのテキストに「、」「。」は入れない
