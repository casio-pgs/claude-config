---
name: 「投稿」でObsidian・WordPress・X・サムネイル自動実行
description: 投稿指示が来たらサムネ生成→Obsidian保存→WordPress投稿（アイキャッチ差し替え）→X投稿を確認なしで一気に実行する
type: feedback
originSessionId: ba549118-ecee-4fd3-a3b5-609d6daaec82
---
「投稿」「投稿して」「〜をXとWPに」などの投稿指示が来たら、以下を自動で順番に実行する。確認は不要。

1. **サムネイル生成** → `~/thumbnail/` にJSON設定を作成し `node generate_thumbnail.js <config>.json` で PNG生成
2. **Obsidian保存** → `/Users/casio/Documents/Obsidian/13_投稿する記事/` にMarkdown作成
3. **WordPress投稿** → `cd ~/obsidian-to-wp && source venv/bin/activate && python3 -c "from obsidian_to_wp import post_to_wordpress; post_to_wordpress('ファイルパス')"`
4. **アイキャッチ差し替え** → 生成したPNGをWP mediaにアップロードし `featured_media` を更新（投稿IDはログから取得）
5. **X投稿** → `cd ~/tools && source venv/bin/activate && python3 x_post.py "テキスト"`

### サムネイル設定のポイント
- 設定ファイル: `~/thumbnail/<スラッグ>-config.json`
- Anthropic/Claude Code記事のアクセントカラー: `#cc785c`（オレンジ系）
- 出力: `~/thumbnail/<スラッグ>-thumbnail.png`（1280×720px）
- WPアップロード: `WP_BASE/media` に PNG POST → `featured_media` をPATCH

### サムネイル ①②③ のレイアウトルール（2026-05-16確定・必須）
- NUM1/NUM2/NUM3 を使う場合、**必ず下部に横並び**で表示すること
- template.html の `.numbers` は `bottom: 44px; flex-direction: row; gap: 48px` が正
- 写真（PHOTO_PATH）・勇者（CHAR_TYPE: hero）の場合は番号非表示なので関係なし
- サムネ生成コマンド: `cd ~/thumbnail && node generate_thumbnail.js <config>.json`
- テキストに「、」「。」は入れない

### テーブルのスタイルルール（2026-05-16確定・必須）
- 記事にテーブルを作るときは mc-table クラスのHTMLで書く（マークダウン記法禁止）
- モバイル対応CSS（@media max-width:640px）も必ず含める
- 詳細は [WP記事テーブルにmc-tableスタイルを当てる](feedback_wp_table_style.md) を参照

X投稿のテキストは記事本文から適切に抜粋・編集してまとめる（130〜280字目安）。

**Why:** 毎回の手動サムネ・投稿作業をワンフローに統合したい（2026-05-16）。
**How to apply:** 「投稿」「記事にして」「WPとXに」などの指示で即発動。長文テキストが来た場合も同様。
