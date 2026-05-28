---
id: workspace.2026-05-note-production-pilot.06_surface_design.v1
status: active
slug: 2026-05-note-production-pilot
---

# 06_surface_design.md — UI への見せ方

## 役割

`co-note-production` が CompanyOS UI / Topology Studio に **どう見えるか** を 3 surface について具体に設計する。

## 持つもの

- 3 surface（repo_card / workflow_lens / member_work_lens）それぞれの表示要素
- 各 surface の source_pin
- MNP block の方針（本 pilot では使わない）

## 持たないもの

- surface 実装コード（→ Phase 3）
- exporter 実装（→ MVP 範囲外）

---

## Surface 1: `repo_card.surface.md`

### 役割

CompanyOS Repo Card / Topology Studio のノードとして `co-note-production` を表示する。

### 表示要素

- repo 名: `co-note-production`
- archetype アイコン / ラベル: `note_production_repo`
- version（SPOKE.yml から）
- 進行中 workflow 数
- 進行中 task 数
- 月次公開本数
- 最終更新日時（freshness）

### 表示しないもの

- 記事タイトル詳細（→ workflow_lens 側）
- 著者名
- 未公開記事一覧

### source_pin

| 情報 | pin |
| --- | --- |
| repo 名 / archetype / version | `../../README.md`, `../../SPOKE.yml` |
| 進行中 workflow / task 数 | `../../20_workspace/articles/*/meta.md`（集計） |
| 月次公開本数 | `../../99_publish_history/{YYYY-MM}.md`（集計） |

### MNP block の方針

- 本 pilot では **書かない**（installed/ 昇格前）
- 将来 MNP block を入れる場合は `contract.mnp_surface.v1` の制約を満たす

---

## Surface 2: `workflow_lens.surface.md`

### 役割

note 制作 workflow（企画→執筆→レビュー→公開→学習）の進行状態を Workflow Lens として表示する。

### 表示要素

- workflow ごとの phase 進行（lane / column）
- 各 phase の active 記事カード（タイトル / status badge / next_action / owner）
- workflow 全体の集計（active 件数 / publish_ready 件数）

### lane 構成（`semantic.workflow_status.v1` の 8 enum から）

```
planned        →  予定
active         →  進行中
review_needed  →  レビュー待ち
publish_ready  →  公開準備 OK
published      →  公開済み
learning       →  学習中
（blocked / archived は別フィルタで表示）
```

### 表示しないもの

- **記事本文の draft**
- 未公開メモ
- 著者個人の感想 / feedback 原本

### source_pin

| 情報 | pin |
| --- | --- |
| workflow 定義 | `../../02_workflows/note_article_production.md` |
| 各記事の進行状態 | `../../20_workspace/articles/*/meta.md` |
| phase / status enum | V4 `semantic.workflow_status.v1`（ID 参照、`co-harness-designer-v4/03_status_metrics/10_workflow_status.md`） |

### MNP block の方針

本 pilot では **書かない**。将来 MNP installed/ 昇格後に書く場合は以下を満たす：

- source 属性必須
- status は 8 enum のみ
- 記事本文を含めない（MNP Not SSOT Gate）

---

## Surface 3: `member_work_lens.surface.md`

### 役割

owner（saku 等）視点で「今日やる仕事」を Member Work Lens として表示する。

### 表示要素

- owner 別の active task list（記事タイトル / next_action / due / status badge）
- 関連 repo タグ（`co-note-production`）

### 表示しないもの

- 記事本文の draft / 未公開メモ
- 他 archetype repo（client_repo / future archetype）の task — 本 surface は note_production_repo 専用

### source_pin

| 情報 | pin |
| --- | --- |
| owner 別の active task | `../../20_workspace/articles/*/meta.md`（owner で grep） |
| next_action / due | 同上 |

### MNP block の方針

本 pilot では **書かない**。将来 MNP installed/ 昇格後の writeback フローは：

```
UI 編集 → serialize → MNP → contract.writeback.v1 → writeback intent → 人間承認 → meta.md 更新
```

直接書き戻しは禁止（contract.writeback.v1 planned stub の制約）。

---

## 全体方針（3 surface 共通）

### 業務正本の保護（最重要）

| 業務正本 | 保護方針 |
| --- | --- |
| 記事本文 (`draft.md`) | `.companyos/` 内には絶対に持たない |
| 記事 meta (`meta.md`) | source_pin から参照のみ、本文を copy しない |
| 公開後コンテンツ | 公開済み状態 / URL のみ surface 表示、本文は持たない |
| 未公開メモ | 一切 expose しない |

### source_pin の必須化

全 surface の **全表示要素**に source_pin が必要（Source Pin Gate）。
source_pin がない要素は Phase 3 で Critical Gate で止める。

### frontmatter での source_pin の表記（重要）

`contract.surface.v1`（`../../../02_contracts/40_surface_contract.md`）は、surface ファイルの frontmatter に **`source_pins:`（複数形）の YAML 配列** を要求する。

本設計書（本 pilot package）では各 surface の source 情報を表形式で列挙しているが、Phase 3 で実 `*.surface.md` を書き起こすときは、frontmatter の key を **必ず `source_pins:`（複数形 / s 付き）** とする。

例（Phase 3 で書く形）:

```yaml
---
id: surface.repo_card.v1
status: active
source_pins:
  - path: "../../README.md"
    field: "title"
  - path: "../../SPOKE.yml"
    field: "archetype, version"
  - path: "../../20_workspace/articles/*/meta.md"
    field: "active_workflows, active_tasks"
---
```

`source_pin:`（単数形）と書くと contract 違反。実装 AI / 人間は frontmatter key の複数形化を必ず確認。

### status / next_action の運用

- status は `semantic.workflow_status.v1` の 8 enum のみ
- CompanyOS UI 投影時は 5 enum へ変換（mapping_rules、Phase 3 以降で詳細）
- next_action は自然文（80 文字以内推奨）

## 関連ファイル

- `05_contract_design.md`
- `04_directory_design.md`
- `../../../02_contracts/40_surface_contract.md`
- `../../../03_status_metrics/10_workflow_status.md`
- `../../../06_build/scaffolds/companyos_interface/surfaces/`（雛形）
