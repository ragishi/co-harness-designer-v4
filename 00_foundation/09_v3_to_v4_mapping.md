---
id: foundation.v3_to_v4_mapping.v1
status: active
owner: 00_foundation
note: "V3 構造 → V4 構造の対応表。V3 本体はコピーせず pointer のみ。"
---

# 09_v3_to_v4_mapping.md — V3 構造 → V4 構造の対応表

## 役割

V3（co-harness-design-v3）の構造が V4 のどの root に対応するかの対応表。V3 を知る人間・AI が V4 を読むときの橋渡しと、なぜ V4 が構造を変えたのかの説明責任を果たす。

V3 本体はコピーしない。pointer のみ（local path: `/Users/saku/co-harness-design-v3/`）。

## V3 root → V4 root 対応表

| V3 | 役割 (V3) | V4 の対応先 |
| --- | --- | --- |
| `00_foundation/` | WHY・設計思想・governance | `00_foundation/`（継承）＋ `01_principles` / `04_decision_rules` |
| `01_process/` | WHEN+ORDER・phase / workflow | `04_archetypes/workflows/` ＋ `02_contracts/20_workflow_contract.md` |
| `02_quality_standards/` | WHAT GOOD MEANS・gate / standard | `07_quality/` |
| `03_use_profiles/` | FOR WHO・profile | `04_archetypes/`（profile→archetype に昇格）＋ `05_read_sets/` |
| `04_runtime/` | HOW AI EXECUTES・runtime | `CLAUDE.md` ＋ `.claude/` `.codex/` `.github/` ＋ `05_read_sets/` |
| `10_knowledge/` | 知識 | `10_references/` ＋ `01_meaning_model/` |
| `11_connect/` | 外接続 | `11_connect/`（継承） |
| `20_workspace/` | 作業中 | `20_workspace/`（継承） |
| `21_outputs/` | 完成物 | `21_outputs/`（継承） |
| `30_feedback/` | 生の観測 | `30_feedback/`（**番号継承**） |
| `31_learning/` | 抽象化された学び | `31_learning/`（**番号継承**） |
| `40_extension/` | 後付け拡張 | `40_extensions/`（継承） |
| `90_archive/` | 退役 | `90_archive/`（継承） |

## V4 で新設した root（V3 になし）

- `01_meaning_model/` — 意味モデル（entity / relationship）。V3 で `10_knowledge` に混在していた概念を独立 root 化。
- `02_contracts/` — CompanyOS への投影契約。V4 が「target repo を産み UI に繋ぐ factory」になり新設。
- `03_status_metrics/` — 状態・指標（status enum / sync 鮮度）。投影に必要な状態語彙を独立化。
- `06_build/` — scaffold / exporter。target repo 生成と `.companyos/` 投影のため新設。

## V4 が V3 から変えた点と意図

- **archetype 中核化**: V3 の `03_use_profiles`（profile）を、目的別 Repo 原型 `04_archetypes/` に昇格し V4 の中核に置いた。
- **contracts 統合 + status / build 新設**: 「設計 OS」から「target repo を産み CompanyOS UI に投影する factory」へ目的が拡張したため。
- **read_sets 採用**: V3 の read set 概念を `05_read_sets/` として独立 root 化（`05_context_packs` は不採用）。
- **30 / 31 の番号継承**: feedback ⇄ learning の分離と番号を V3 から維持（V3 連続性・Absolute Rule 5）。
- **DRR / L0–L4 / migration**: V3 の判断軸を `04_decision_rules.md` に集約。

## 持たないもの

- V3 本体の内容コピー（→ pointer `/Users/saku/co-harness-design-v3/`、`../90_archive/99_legacy_v3_pointer.md`）
- 外部参考 pin の管理（→ `../10_references/source_pins.md` §3 V3）
- V4 の設計原則本体（→ `01_principles.md`）

## 最低 acceptance

- V3 の各 root が V4 のどこに対応するか表で読める
- V4 が新設した root と、変更の意図が読める

## 止める条件

- V3 本体の内容をここにコピーし始める（pointer 原則の違反）
- V4 の設計原則本体をここに重複定義する

## 関連ファイル

- `../90_archive/99_legacy_v3_pointer.md`
- `../10_references/source_pins.md`（§3 V3）
- `01_principles.md`
