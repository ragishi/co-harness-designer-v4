# 10_entities.md — V4 の主要 entity

## 役割

V4 が扱う主要 entity（概念）と、その関係・属性・ルールを Markdown で定義する。

prompt / workflow / harness はここの entity を ID で参照する（定義をコピーしない）。

## 持つもの

- 16 entity の定義
- 主要な関係（自然文）
- 推論ルール（最小限）

## 持たないもの

- 計算式（→ `../03_status_metrics/`）
- 入出力 schema（→ `../02_contracts/`）
- instance データ

---

## §1. Repo

**ID**: `entity.repo.v1`

**一言**: 特定の目的を持つ作業・成果物・運用情報の正本置き場。

**持つもの**:
- 目的（README で明示）
- workspace（作業中の SSOT）
- outputs（完成物）
- feedback / learning（改善ループ）
- archive（退役保管）
- `.companyos/` interface（CompanyOS 接続口）

**持たないもの**:
- CompanyOS 全体の判断権限
- 他 Repo の成果物正本
- UI 表示用派生 cache の正本

**種別（archetype による分類）**: note_production_repo / client_repo / project_progress_repo / sns_operations_repo / youtube_ops_repo / workflow_ops_repo / prompt_repo / design_system_repo

---

## §2. Workflow

**ID**: `entity.workflow.v1`

**一言**: Repo 内で繰り返し実行される手順の集合。

**持つもの**: 名前と目的 / Phase の連続 / 入出力 / gate（任意） / 関連 prompt と tool

**持たないもの**: 業務正本（Workflow は手順、内容は別 file）

---

## §3. Phase

**ID**: `entity.phase.v1`

**一言**: Workflow を構成する段階。

**持つもの**: 名前と目的 / 次の Phase への遷移条件 / 産む Artifact

---

## §4. Task

**ID**: `entity.task.v1`

**一言**: AI または人が実行する最小単位。

**持つもの**:
- title / summary
- status（`../03_status_metrics/10_workflow_status.md` の enum）
- owner（AI / human / repo のいずれか）
- source_path（業務正本の場所）
- next_action
- quality_gate（任意）

**関係**:
- Task は Workflow に属する
- Task は Owner を持つ
- Task は Artifact を produce する
- Task は Surface に投影される（CompanyOS UI で表示される場合）

**表示用 normalized form**: CompanyOS UI が読む形は `company-os/.../task_source_contract.yml` の `normalized_task_pointer` を ID 参照する。V4 内では再定義しない。

---

## §5. Artifact

**ID**: `entity.artifact.v1`

**一言**: Workflow / Task が産む成果物。

**持つもの**: path（業務正本の場所） / type / status / source_pin（generated の場合）

---

## §6. Surface

**ID**: `entity.surface.v1`

**一言**: Repo 正本を CompanyOS UI に表示するための見せ方。

**重要**: **Surface は正本ではない**。Surface は業務正本（Markdown）から生成・参照される。

詳細契約: `../02_contracts/40_surface_contract.md`

---

## §7. Lens

**ID**: `entity.lens.v1`

**一言**: CompanyOS UI 上の view / レンズ表示。

**例**: Workflow Lens / Member Work Lens / Topology Lens / Repo Card

Surface が Lens のために生成される。

---

## §8. Prompt

**ID**: `entity.prompt.v1`

**一言**: AI への指示文。

**重要**: **Prompt は SSOT を内包しない**（P0' ID 参照原則）。必要な定義は entity / metric / contract の ID 参照を書く。

---

## §9. CompanyOS

**ID**: `entity.companyos.v1`

**一言**: Hub。UI / 接続契約 / 権限を所有。

**関係**: 全 V4 と target repo は CompanyOS に attach される（`SPOKE.yml` で binding）。CompanyOS は projection_registry で各 repo の表示先を所有。

---

## §10. Project Progress Repo

**ID**: `archetype.project_progress_repo.v1`（archetype として `04_archetypes/repo/` 側で詳細）

**一言**: WBS / 進捗 / milestone を所有する target repo の archetype。

---

## §11. Owner Repo

**ID**: `archetype.owner_repo.v1`

**一言**: 成果物正本を持つ target repo の archetype。note_production_repo / youtube_ops_repo / sns_operations_repo などが該当。

---

## §12. Client Repo

**ID**: `archetype.client_repo.v1`

**一言**: クライアント案件を扱う target repo の archetype。

詳細: `../04_archetypes/repo/client_repo.md`

---

## §13. Read Set

**ID**: `entity.read_set.v1`

**一言**: 特定の作業のために AI / UI が読むべき file の順序付きリスト。

**持つもの**: 読む順番 / 読まないもの（明示） / 関連 archetype

詳細: `../05_read_sets/`

---

## §14. Extension

**ID**: `entity.extension.v1`

**一言**: 後付けされる機能 pack。

**種別**:
- `installed/` — 採用済み
- `proposals/` — pilot 中

詳細: `../40_extensions/`

---

## §15. Archetype

**ID**: `entity.archetype.v1`

**一言**: 目的別 Repo の「型」。

**持つもの**: 必須 module / 推奨 module / 推奨構造 / quality_profile

詳細: `../04_archetypes/00_archetype_framework.md`

---

## §16. MNP Surface

**ID**: `entity.mnp_surface.v1`

**一言**: UI 状態を AI が編集しやすい中間記法で表したもの。

**重要**: **MNP Surface は業務正本ではない**。Markdown 正本から生成され、UI に投影される中間表現。

詳細契約: `../02_contracts/80_mnp_surface_contract.md`

---

## 主要な関係（自然文）

- Repo は Workflow を含む
- Workflow は Phase の連続を含む
- Phase は Task を含む
- Task は Owner を持つ（AI / human / repo）
- Task は Artifact を produce する
- Task は Surface に投影される（CompanyOS UI で表示される場合）
- Workflow / Task は Prompt を使うことがある（Prompt は SSOT を内包しない）
- Repo は CompanyOS に attach される
- Archetype は Repo の型を定義する
- Extension は Archetype に depends_on されることがある（archetype → extension の一方向）

## 推論ルール（最小限）

- source_pin がない generated artifact は信頼しない（low_confidence）
- ssot_index に存在しない ID を参照する出力は `ssot_violation`
- 業務正本（記事本文等）が `.companyos/` 内にあれば policy 違反
- MNP block が `.companyos/surfaces/` 外で使われたら policy 違反

## 関連ファイル

- `00_glossary.md`
- `../02_contracts/00_contract_map.md`
- `../03_status_metrics/10_workflow_status.md`
- `../04_archetypes/00_archetype_framework.md`

## 最低 acceptance

- 16 entity が記載されている
- 主要 5 概念（Repo / Workflow / Task / Artifact / Surface）に「持つもの / 持たないもの」がある
- 主要関係が自然文で読める
- 推論ルールが最小限ある

## 止める条件

- entity に metric 計算式が混入した
- entity を YAML schema で割り始めた
- business 固有用語（"YouTube のサムネ" 等）が混入した
- 関係が双方向になった（書き戻し path が許可された）
