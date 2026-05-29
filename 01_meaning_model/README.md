# 01_meaning_model/ — 意味モデル

## 0. 30 秒で分かる役割

Atlan でいう **オントロジー相当**。V4 の中で扱う **概念・関係・推論ルール** を Markdown で定義する。

専門用語 "ontology" を直接 root 名にしない（人間の直感を優先して "meaning_model" と翻訳）。

## 1. このrootが持つもの

- glossary（用語集）
- entity 定義（Repo / Workflow / Task / Artifact / Surface / ...）
- relationship 定義（has, produces, evaluates, satisfies, ...）
- taxonomies（task_type / risk_level / archetype tag）
- rules（推論ルール、最小限）

## 2. このrootが持たないもの

- 指標の計算式（→ `../03_status_metrics/`）
- 入出力 schema（→ `../02_contracts/`）
- 個別 prompt
- instance データ

## 3. File Map

| path | 役割 |
| --- | --- |
| `README.md` | この入口 |
| `feedback.md` | meaning_model への改善メモ |
| `00_glossary.md` | 用語の入口 |
| `01_plain_language_glossary.md` | 平易な言い換え集（初学者向け・pointer-only） |
| `10_entities.md` | entity 定義（V4 の主要 16 概念） |
| `20_relationships.md` | relationship 定義（planned stub） |
| `30_taxonomies.md` | taxonomies（task_type / risk_level / archetype tag）（planned stub） |
| `40_rules.md` | 推論ルール（最小限）（planned stub） |

MVP では entity を 1 ファイル（`10_entities.md`）に集約。サブ分割（`20_relationships.md` / `30_taxonomies.md` / `40_rules.md`）は住所のみ確保した planned stub であり、本格分割は使いながら判断。

## 4. 読む順番

1. `README.md`
2. `00_glossary.md`（用語の入口）
3. `10_entities.md`（entity 本体）

## 5. 最低 acceptance

- glossary が存在し、主要 5 概念（Repo / Workflow / Task / Artifact / Surface）が読める
- entity 定義が Markdown で読める形式
- 各 entity に「持つもの / 持たないもの」が書かれている

## 6. 止める条件

- entity を YAML schema で深く割って書き始めた（Markdown-first 違反）
- ontology の本文に metric 計算式が混入した
- prompt 本文がここに置かれた

## 7. 関連 root

- `../02_contracts/` — 約束（entity を「どう運ぶか」）
- `../03_status_metrics/` — 状態・指標（entity の「測定」）
- `../05_read_sets/` — entity を読む順番
