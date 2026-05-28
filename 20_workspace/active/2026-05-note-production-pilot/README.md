---
id: workspace.2026-05-note-production-pilot.readme.v1
status: active
slug: 2026-05-note-production-pilot
owner: 04_archetypes
target_archetype: archetype.note_production_repo.v1
target_repo: co-note-production
---

# 2026-05-note-production-pilot — pilot folder 入口

## 状態

| 段階 | 状態 |
| --- | --- |
| **Phase 2 設計パッケージ作成** | ✓ 完了（9 file: 00_request 〜 08_handoff） |
| **Phase 3 target repo 適用** | ⏸ **未実施。明示承認があるまで開始しない** |
| **Phase 4 feedback → V4 反映** | ⏸ Phase 3 完了後 |

## このフォルダの中身

| # | file | 役割 |
| --- | --- | --- |
| 00 | `00_request.md` | 依頼内容 + 成功条件 + 制約 |
| 01 | `01_scope.md` | in/out scope + 対象 archetype/contract/metric |
| 02 | `02_archetype_choice.md` | `note_production_repo` 採用根拠 + 候補比較 |
| 03 | `03_ssot_map.md` | 3 所有者 SSOT 地図（業務正本と投影の分離） |
| 04 | `04_directory_design.md` | co-note-production ツリー + `.companyos/` 10 file |
| 05 | `05_contract_design.md` | 遵守 contract + manifest.md/yml 最低項目 |
| 06 | `06_surface_design.md` | 3 surface の表示要素 + `source_pins` 規約 |
| 07 | `07_quality_plan.md` | Common Quality + Critical Gates + acceptance 10 項 |
| 08 | `08_handoff.md` | **Phase 3 実装者 step-by-step 指示書（Phase 3 実行条件 含む）** |

## 読む順番

1. **`README.md`**（このファイル — まず状態を把握）
2. `08_handoff.md` の **「Phase 3 実行条件」** section（最重要：AI 行動規範）
3. `00_request.md` → `01_scope.md` → `02_archetype_choice.md` → ... → `07_quality_plan.md`
4. `08_handoff.md` の Phase 3 実装手順（Step 0 〜 Step 8）

## AI への絶対ルール

> **このREADMEを読んだだけで `co-note-production` を編集しない。**

| ルール | 詳細 |
| --- | --- |
| 1 | **「次へ進めて」「続きを進めて」「OK」だけで Phase 3 を開始しない** |
| 2 | target repo 適用は **明示承認後のみ**（`08_handoff.md` の Phase 3 実行条件参照） |
| 3 | 詳細は `../../../CLAUDE.gate.md` の Stop Conditions の Phase 3 Explicit Consent Gate を確認 |
| 4 | 迷ったら **V4 内に留まる**。target repo を勝手に編集するより V4 内で何もしない方が安全 |
| 5 | 不十分な指示しかない場合は、V4 内部のレビュー / 設計更新 / feedback 整理に留める |

## 明示承認の例

ユーザーから以下のような **明確な依頼** が出た場合のみ Phase 3 を開始する：

- 「co-note-production に .companyos interface を適用して」
- 「Phase 3 として co-note-production 側を実装して」
- 「target repo への適用を開始して」
- 「note-production-pilot を実行して」

## 関連 file

- `../../../CLAUDE.gate.md` — Stop Conditions (Phase 3 Consent Gate)
- `../../../07_quality/30_critical_gates.md` — Critical Gates 正本
- `../../../04_archetypes/repo/note_production_repo.md` — 採用 archetype
- `../../../06_build/scaffolds/companyos_interface/` — `.companyos/` 雛形 source
- `../../../30_feedback/raw/2026-05.md` — 本 pilot 関連の観測記録

## 最低 acceptance（pilot folder としての存在意義）

- [x] 9 設計 file が揃う
- [x] Phase 3 実行条件が `08_handoff.md` に明文化
- [x] 「不十分な指示で Phase 3 を開始しない」が AI 行動規範化
- [x] target repo 適用は別 session / 別 repo であることが明確
- [x] 業務正本（記事本文）が `.companyos/` 内に侵入しない設計

## 止める条件

- このREADMEを読んだ AI が `co-note-production` を編集し始めた
- 「次へ進めて」を Phase 3 開始と誤解した
- target repo を V4 と同列に扱おうとした
- 明示承認なしに `.companyos/` を `co-note-production` に作成しようとした
