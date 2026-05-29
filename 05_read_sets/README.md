# 05_read_sets/ — AI / UI 読書セット

## 0. 30 秒で分かる役割

Atlan でいう **コンテキストレイヤー相当**。作業ごとに、AI や UI が読むべき file の順序付きリストを定義する。

専門用語 "context_packs" を避け、人間の直感を優先して "read_sets" と命名。

## 1. このrootが持つもの

- read_set policy（共通ルール）
- 作業 / archetype 別の read_set（順序付き file list）
- graph/（dependency / relation map、後段）

## 2. このrootが持たないもの

- entity / contract / metric の定義本体（read_set は参照のみ）
- 個別 prompt 本文

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `00_read_set_policy.md` | read_set 共通方針（planned stub） | — 後段 |
| `companyos_repo_design_read_set.md` | CompanyOS 接続 repo 設計時に読む順 | ✓ |
| `project_progress_read_set.md` | project 管理 repo 設計時 | — 後段 |
| `client_repo_read_set.md` | client repo 設計時 | — 後段 |
| `note_production_read_set.md` | note 制作 repo 設計時 | — 後段 |
| `youtube_ops_read_set.md` | YouTube 設計時 | — 後段 |
| `sns_ops_read_set.md` | SNS 設計時 | — 後段 |
| `topology_surface_read_set.md` | Topology Studio / Surface 設計時 | — 後段 |
| `graph/` | dependency / repo / surface relation map | — 後段 |

MVP では 1 read_set のみ。残りは使いながら追加。

## 4. 読む順番

1. `README.md`
2. `companyos_repo_design_read_set.md`

## 5. 最低 acceptance

- 各 read_set に「読む順番」「読まないもの」が書かれている
- 各 read_set が target archetype を宣言している
- read_set 自体に定義本文が混入していない（全て pointer）

## 6. 止める条件

- read_set に entity / contract の本文が直書きされた
- 「全部読む」のような無限の read_set ができた
- archetype を絞らない read_set ができた

## 7. 関連 root

- `../00_foundation/`
- `../01_meaning_model/`
- `../02_contracts/`
- `../03_status_metrics/`
- `../04_archetypes/`
- `../07_quality/`
