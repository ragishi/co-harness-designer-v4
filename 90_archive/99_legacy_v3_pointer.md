---
id: pointer.legacy_v3.v1
status: active
owner: 90_archive
---

# 99_legacy_v3_pointer.md — V3 への明示的 pointer

## 役割

V4 の予約 / V3 との関係を明示する。

## V3 リポジトリ情報

| 項目 | 値 |
| --- | --- |
| repo name | `co-harness-design-v3` |
| local path | `/Users/saku/co-harness-design-v3/` |
| status | `successor_created_not_archived` |
| successor | `co-harness-designer-v4`（このリポジトリ） |
| successor_created_at | 2026-05-28 |

## V3 からの継承一覧

| V3 機構 | V4 での継承先 |
| --- | --- |
| 5-tier 思想（WHY / WHEN+ORDER / WHAT GOOD / FOR WHO / HOW） | `../00_foundation/00_purpose.md`, `01_principles.md` |
| 1 情報 1 住所 | `../00_foundation/02_ssot_authority_map.md` |
| 引き算の美学 | `../00_foundation/04_decision_rules.md`（DRR） |
| `30_feedback/` + `31_learning/` 分離 | `../30_feedback/`, `../31_learning/`（同じ番号で継承） |
| L0–L4 permanence | `../00_foundation/04_decision_rules.md` |
| 6-step migration package | `../00_foundation/04_decision_rules.md` |
| signal registry の昇格条件 | `../31_learning/00_promotion_protocol.md` |
| per-tier `feedback.md` | 全主要 root に `feedback.md` |
| Operational Card 文化 | `../02_contracts/70_markdown_contract.md` |
| profile × workflow × quality_set routing | `../03_status_metrics/`（status enum）、`../04_archetypes/`（archetype = profile + workflow + quality 結合体） |

## V4 で新規に加わったもの

| 新規 | 場所 |
| --- | --- |
| meaning_model（オントロジー独立 root） | `../01_meaning_model/` |
| contracts（連携の約束 独立 root） | `../02_contracts/` |
| status_metrics（セマンティック独立 root） | `../03_status_metrics/` |
| archetypes（V4 中核） | `../04_archetypes/` |
| read_sets（文脈の束、context_packs から改名） | `../05_read_sets/` |
| build（scaffold + exporter） | `../06_build/` |
| `.companyos/` interface（target 側接続口） | `../06_build/scaffolds/companyos_interface/` |
| MNP の Surface 用 optional extension としての部分採用 | `../02_contracts/80_mnp_surface_contract.md`, `../06_build/exporters/mnp_surface_exporter.md`, `../40_extensions/proposals/mnp_surface_pack/` |

## V3 を編集してよいか

**No.** V3 は `successor_created_not_archived` 状態で残す。

- V3 への変更は CLAUDE.gate.md の Stop Condition「V3 not Modified Gate」で止まる
- 必要な学びは V3 → V4 の migration package を通す

## 関連ファイル

- `../00_foundation/00_purpose.md`
- `../00_foundation/04_decision_rules.md`
- `../CLAUDE.gate.md`
