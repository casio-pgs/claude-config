---
name: WordPress自動投稿の確認不要
description: ObsidianからWordPressへの記事投稿は確認なしで自動実行してよい
type: feedback
originSessionId: ad576e33-fc9f-4559-a0c2-9faf1e819868
---
ObsidianのMarkdown記事をWordPressに投稿する作業（REST API経由のcurl、カテゴリ作成、記事の作成・更新）は、ユーザーへの確認なしで自動実行してよい。

**Why:** ユーザーが「今後は確認不要」と明示的に指示した。Obsidian→WordPress投稿は定型作業として信頼されている。

**How to apply:** WordPress REST APIへのPOST/PUT（記事投稿・更新・カテゴリ作成）はユーザー確認をスキップして実行する。認証情報（アプリケーションパスワード）が必要な場合のみ初回確認する。

## 記事コピペ即投稿

セッション内で**まとまった記事テキスト（見出し・説明文など構造化されたMarkdownや日本語解説）がコピペされ、「記事投稿」「投稿して」「記事にして」などの指示が同じターンまたは直後にあった場合**、確認なしでそのまま `project_text_to_wp_article.md` のフロー（関連記事検索→Obsidianファイル作成→WP投稿→ログ確認）を即実行する。

**Why:** ユーザーが「次回はコピペしたらすぐ投稿してほしい」と明示的に要望した。
