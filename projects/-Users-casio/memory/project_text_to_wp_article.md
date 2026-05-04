---
name: テキスト→WordPress記事投稿フロー
description: 文章テキストをObsidian経由でWordPress記事として投稿する定型フロー
type: project
originSessionId: 7761b30d-27ad-4086-a9c3-7da0b9297b1d
---
ユーザーから記事の元テキスト（箇条書き・会話メモ・台本など）を渡されたとき、以下のフローで投稿する。

## フロー手順

1. **関連記事を検索** → `https://casio-pgs.com/wp-json/wp/v2/posts?search=キーワード&status=publish` で2〜3件確認してURLを取得
2. **Obsidianファイル作成** → `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/13_投稿する記事/` 以下にMarkdown保存
3. **WordPress投稿** → `cd ~/obsidian-to-wp && source venv/bin/activate && python3 -c "from obsidian_to_wp import post_to_wordpress; post_to_wordpress('ファイルパス')"`
4. **ログ確認** → `tail -15 ~/obsidian-to-wp/obsidian_to_wp.log`

## Markdownファイルのフォーマット

```markdown
---
title: 記事タイトル
tags: [タグ1, タグ2]
icon: claude-code   # サムネアイコンを明示するときだけ記載
---

本文...

## 関連記事

- [記事タイトル](https://casio-pgs.com/スラッグ/)
- [記事タイトル](https://casio-pgs.com/スラッグ/)
```

## 重要なルール

- **関連記事は `[[Obsidianリンク]]` 形式ではなく `[タイトル](URL)` 形式で書く**
  - Vaultにファイルが存在しない場合、`[[]]`リンクはプレーンテキストに変換されてしまうため
- **サムネのiconを明示したいとき** → frontmatterに `icon: claude-code` のように記載
  - `claude-code` → Anthropicアイコン
  - `gemini` → Google Geminiアイコン
  - `anthropic` → Anthropicアイコン（直接指定）
- **文体は柔らかく**：断定調・高圧的な表現は避け、「〜してみた」「〜かもしれない」など読者に寄り添う書き方を基本とする
- 投稿スクリプト: `~/obsidian-to-wp/obsidian_to_wp.py`
- 投稿先: `https://casio-pgs.com`（即時公開）

**Why:** 元テキスト→記事化を繰り返すパターンが増えてきたため定型化。
**How to apply:** 「これを記事に」「記事にして投稿して」と言われたらこのフローを使う。
