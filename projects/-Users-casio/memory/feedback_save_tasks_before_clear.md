---
name: /clear前にタスクを記憶する
description: /clearを実行する前に、進行中のタスクをメモリに保存する
type: feedback
originSessionId: 8e657a4d-d95b-4ca8-b224-050778bb7fe6
---
/clear の前には、現在進行中・未完了のタスクをメモリファイルに保存してから実行する。

**Why:** 会話がリセットされてもタスクの状態を引き継げるようにするため。

**How to apply:** ユーザーが /clear しようとしているとき、またはこちらから clear を提案するときは、必ずその前にタスク一覧をメモリに書き出す。
