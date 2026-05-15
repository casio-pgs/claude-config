---
name: WP記事テーブルにmc-tableスタイルを当てる
description: WordPress記事にテーブルを作るときは必ずmc-tableクラスのスタイルを適用する
type: feedback
originSessionId: da1fbb27-63af-42e6-adbd-1a7f69344040
---
記事内にテーブルを作成する際は、必ず以下のスタイルを付けてHTMLで書く。マークダウンのテーブル記法は使わない。

**Why:** 後から差し替えが必要になったため、最初からスタイル済みで作成するようにする（2026-05-16）

**How to apply:** Obsidianファイル作成時点でテーブルをこのHTMLで記述する。

```html
<style>
.mc-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 15px;
  margin: 1.5em 0;
}
.mc-table th,
.mc-table td {
  border: 1px solid #ccc;
  padding: 10px 14px;
  text-align: left;
  vertical-align: middle;
}
.mc-table thead tr {
  background-color: #1b5e20;
  color: #fff;
}
.mc-table thead th:first-child {
  background-color: #145214;
}
.mc-table tbody tr:nth-child(odd) {
  background-color: #f4fbf5;
}
.mc-table tbody tr:nth-child(even) {
  background-color: #ffffff;
}
.mc-table tbody td:first-child {
  font-weight: bold;
  background-color: #e8f5e9;
  color: #2e7d32;
  white-space: nowrap;
}
</style>

<table class="mc-table">
  <thead>
    <tr>
      <th>列1</th>
      <th>列2</th>
      <th>列3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
  </tbody>
</table>
```
