---
id: workspace.2026-05-note-production-pilot.03_ssot_map.v1
status: active
slug: 2026-05-note-production-pilot
---

# 03_ssot_map.md — 正本の置き場所

## 役割

`co-note-production` の **正本住所地図**を作る。3 所有者（company-os / V4 / target）で正本を割り振り、`.companyos/` が業務正本を持たないことを構造で示す。

## 持つもの

- 何の正本がどこにあるか（target / V4 / company-os の 3 所有者別）
- 業務正本と投影の分離

## 持たないもの

- 個別 file の中身
- exporter 実装

---

## 3 所有者地図（本 pilot の場合）

### company-os が所有

| 何 | どこ |
| --- | --- |
| 正準 task 契約 (`normalized_task_pointer`) | `company-os/11_connect/contracts/current/task_source_contract.yml` |
| projection 先一覧 | `company-os/11_connect/contracts/current/projection_registry.yml` |
| UI レイアウト | company-os 側 |
| status enum (CompanyOS 側 5: `todo / in_progress / blocked / review / done`) | `task_source_contract.yml` 内 |

### V4 が所有（meta-blueprint）

| 何 | どこ |
| --- | --- |
| `archetype.note_production_repo.v1` 定義 | `co-harness-designer-v4/04_archetypes/repo/note_production_repo.md` |
| `contract.repo.v1` ほか contract 群 | `co-harness-designer-v4/02_contracts/` |
| `semantic.workflow_status.v1`（8 enum） | `co-harness-designer-v4/03_status_metrics/10_workflow_status.md` |
| `.companyos/` scaffold 雛形 | `co-harness-designer-v4/06_build/scaffolds/companyos_interface/` |
| Critical Gates | `co-harness-designer-v4/07_quality/30_critical_gates.md` |

V4 は instance を持たない。target が ID 参照する。

### target repo (`co-note-production`) が所有 — **本 pilot の中心**

| 何 | どこ（target repo 内 path） |
| --- | --- |
| **記事本文の正本** | `20_workspace/articles/{slug}/draft.md` などの archetype 固有 root |
| **記事 meta** | `20_workspace/articles/{slug}/meta.md` |
| workflow 定義 | `02_workflows/note_article_production.md` |
| 接続契約（spoke）の identity | `SPOKE.yml` |
| **CompanyOS 表示 surface 定義** | `.companyos/surfaces/*.surface.md` |
| **source_pin（surface の出自）** | `.companyos/sync/source_pin.md` |
| freshness / generated_from | `.companyos/sync/freshness.md` / `generated_from.md` |
| 再生成 cache（**正本ではない**） | `.companyos/generated/`（README のみ） |
| feedback 原本 | `30_feedback/raw/{YYYY-MM}.md` |
| 学び（curated） | `31_learning/` |

## 業務正本と投影の分離原則（本 pilot で構造に出す）

```
[業務正本]                          [投影]
target repo の通常 dir              target repo の .companyos/
─────────────────────────           ─────────────────────────
20_workspace/articles/.../draft.md   surfaces/repo_card.surface.md
20_workspace/articles/.../meta.md     ←──── source_pin で参照
02_workflows/note_article_*.md       surfaces/workflow_lens.surface.md
                                     ←──── source_pin で参照
                                     generated/（再生成可能 cache のみ）

← V4 P0: "Repo = SSOT, UI = projected view" を構造で表現
```

## 参照方向（一方向、書き戻し禁止）

```
target 業務正本 ──source_pin──> .companyos/surfaces/ ──exporter (Phase 3 以降)──> CompanyOS UI
        ↑
        └─ UI からの書き戻しは禁止（contract.writeback.v1 planned stub、本 pilot 範囲外）
```

UI の変更を反映する場合は **writeback intent → 人間承認 → 業務正本更新** の経路を後段で設計する。

## 関連ファイル

- `02_archetype_choice.md`
- `04_directory_design.md`（この SSOT 地図を物理 dir に落とす）
- `../../../00_foundation/02_ssot_authority_map.md`（V4 の 3 所有者地図）
- `../../../02_contracts/40_surface_contract.md`
- `../../../02_contracts/10_repo_contract.md`
