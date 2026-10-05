# data/biz.json の項目

日時は日本時間のISO形式(`2026-10-05T14:30:00+09:00`)、日付だけの項目は `2026-10-05` の形です。

## 最上位
| 項目 | 内容 |
|---|---|
| `schema` | 形式のバージョン(1) |
| `meta` | `name`(画面の名前)、`stages`(工程の並び)、`decisionDays`(出品から撤退を判断するまでの日数)、`updatedAt` |
| `products` | 商品の一覧 |
| `tasks` | タスクの一覧(Claude Codeへの依頼を含む) |
| `tools` | ツール探索の一覧 |
| `intel` | 情報収集の一覧 |
| `log` | 活動ログ。`{at, who, text}`。`who` は `me` / `claude` / `system` |
| `deleted` | 削除した項目の `{id, at}`。画面との同期で復活させないために使う |

どの項目にも `id` / `createdAt` / `updatedAt` があります。`sample: true` はサンプルです。

## products(商品)
| 項目 | 内容 |
|---|---|
| `name` | 商品名 |
| `kind` | テンプレ / 計算機・ツール / PDF・教材 / 拡張機能 / 開発者向け / サイト・データ / その他 |
| `market` | `JP` / `EN` / `JP+EN` |
| `channel` | 販売先(Etsy、BOOTH、自サイトなど) |
| `stage` | `meta.stages` のどれか、または `撤退` |
| `stageAt` | いまの工程に入った日(YYYY-MM-DD) |
| `price` / `currency` | 価格と通貨(`JPY` / `USD`) |
| `url` | 販売ページ |
| `listedAt` | 出品日(YYYY-MM-DD)。出品から `decisionDays` 日たって `sales` が0だと「判断日」になる |
| `sales` / `revenue` | 累計の販売数と売上 |
| `niche` | ニッチ・キーワード |
| `folder` | 成果物のフォルダ(`products/...`) |
| `notes` | メモ |
| `checklist` | リリース前チェック。`{text, done}` の配列 |

## tasks(タスク・依頼)
| 項目 | 内容 |
|---|---|
| `title` | タイトル |
| `status` | `todo`(未着手) / `doing`(進行中) / `done`(完了) |
| `assignee` | `me`(自分) / `claude`(Claude Code) |
| `kind` | `research`(調査) / `build`(制作) / `write`(文章) / `review`(検算・確認) / `other` |
| `priority` | `high` / `mid` / `low` |
| `due` | 期限(YYYY-MM-DD) |
| `ref` | 関連する項目。`product:<id>` / `tool:<id>` / `intel:<id>` / 空 |
| `notes` | 指示・メモ(Claudeへの指示はここ) |
| `result` | 結果。**Claude Codeが処理後にここへ書く** |
| `doneAt` | 完了日時 |

## tools(ツール)
`name`、`category`(販売先 / 決済 / 集客・SEO / 制作 / 自動化 / アフィリエイト / 分析 / その他)、`status`(気になる / 試用中 / 採用 / 不採用)、`url`、`cost`(料金・手数料)、`pros`、`cons`、`affiliate`、`notes`

## intel(情報)
`title`、`type`(アイデア / 競合・市場 / キーワード / 規約・注意 / ニュース / メモ)、`status`(新着 / 確認済 / 活用済)、`url`、`summary`(要点)、`notes`、`tags`(文字列の配列)、`rating`(0〜3、使える度)、`source`(`me` / `claude`)
