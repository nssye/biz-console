---
name: biz-product-new
description: 新しい商品を data/biz.json に追加し、成果物フォルダの雛形を作る。利用者が /biz-product-new と入力したとき、または商品を追加してと頼まれたときに使う。
---

# 商品の追加

引数に商品名やニッチがあればそれを使う。足りない項目(種類・市場・販売先)は、1回だけまとめて聞く。

## 手順
1. `CLAUDE.md` と `docs/SCHEMA.md` を読む。
2. 半角英数・ハイフンのスラッグを決める(例: `invoice-tracker-en`)。
3. `data/biz.json` の `products` に新しい商品を足す。
   - `id`: `p-` + 英数字8文字、`stage`: `meta.stages` の最初、`stageAt`: 今日、`sales`/`revenue`/`price`: 0
   - `folder`: `products/<スラッグ>`
   - `checklist`: 次の8項目を `done: false` で入れる
     需要を確認した(検索数・競合) / 他者の著作物・過去問を使っていない / 計算式・数値を検算した / 日本語版/英語版の用意 / 特商法・規約・免責の表記 / 出品文・タグ・サムネ / アフィリンクに広告表記を入れた / 判断日(出品から60日)をカレンダーに入れた
4. `products/<スラッグ>/README.md` を作り、商品名・狙う検索キーワード・想定する買い手・作るもの・注意点(権利・検算)を書く。
5. `log` に「商品を追加: <name>」を足す。
6. 次の一手として、調査のタスク(`assignee: "claude"`、`kind: "research"`、`ref: "product:<id>"`)を1件だけ提案し、利用者がよければ追加する。
