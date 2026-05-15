---
name: 「メンテして」でWP/Obsidian同期フロー実行
description: 「メンテして」と言われたらObsidian-WordPress同期メンテフローを即実行する
type: feedback
originSessionId: f7bb0820-41d0-440c-bfe0-4dfa2f782afa
---
「メンテして」「メンテナンスして」「wp メンテ」などの短いトリガーが来たら、確認なしで以下を即実行する。

```bash
bash ~/obsidian-to-wp/wp_maintenance_flow.sh
```

**フロー内容:**
1. `wp_maintenance.py` — WP記事の関連記事リンクを修正・追加
2. `wp_to_obsidian.py` — WPにあってObsidianにない記事を逆インポート

**Why:** 毎回「あのスクリプトを実行して」と説明しなくて済むよう、短いトリガーで即実行できるようにしたい。

**How to apply:** 「メンテして」系の一言が来たら、メモリのメンテナンス（consolidate-memory）ではなくこのシェルスクリプトを実行する。メモリ整理をしたい場合はユーザーが明示的に「メモリをメンテして」「記憶を整理して」と言う。
