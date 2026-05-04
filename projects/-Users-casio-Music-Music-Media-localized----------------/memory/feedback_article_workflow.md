---
name: Obsidian記事作成ワークフロー
description: ユーザーとの会話内容を記事化してObsidianに保存する定型フロー
type: feedback
originSessionId: 2120f6e9-5083-42d4-84de-108fa3b61dc5
---
会話で話し合ったトピックを、以下の形式でMarkdown記事にまとめてObsidianに保存する。

**保存先:** `/Users/casio/Library/Mobile Documents/iCloud~md~obsidian/Documents/Sisan/`

**ファイル名:** スラッグ名.md（例: `ai-seo-considerations.md`）

**フロントマター必須項目:**
- `slug`: 英語のスラッグ名
- `title`: 日本語タイトル
- `description`: 概要文（1〜2文）
- `date`: 作成日
- `tags`: 関連キーワードのリスト
- `thumbnail`: `/images/{slug}-thumb.png`（画像は別途生成）

**Why:** ユーザーがClaudeとの会話内容をObsidianでブログ記事として蓄積・管理したい。

**How to apply:** ユーザーが「記事にして」「Obsidianに保存して」と言ったとき、または会話のまとめを求めたときに、このフローで自動的に記事を作成・保存する。
