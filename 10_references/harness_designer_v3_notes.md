---
id: reference.harness_designer_v3_notes.v1
status: planned
owner: 10_references
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# harness_designer_v3_notes.md — Harness Designer V3 深掘りノート

## 役割

Harness Designer V3（co-harness-design-v3）の構造・思想の深掘りメモを置く場所です。出典管理は `source_pins.md` §3 に委譲しており、本 file は V3 から V4 への継承・変更点の詳細な参考メモを後段で整理する場所として住所を確保します。**本 file は V4 の正本ではありません**。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`00_foundation/09_v3_to_v4_mapping.md` の詳細検討が必要になった段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- V3 の 5-tier core 構造（00_foundation / 01_process / 02_quality_standards / 03_use_profiles / 04_runtime）の参考メモ
- V3 から V4 へ継承した要素の詳細（30_feedback/31_learning 分離、DRR、L0–L4 等）
- V3 から V4 で変えた点の参考メモ（archetype 中核化、.companyos/ 新設等）
- V3 の signal registry lifecycle の参考メモ

## 持たないもの

- 出典表（repo / local path / 参照開始日）→ `source_pins.md` §3 を参照
- V4 正本の V3 継承部分（→ `../00_foundation/01_principles.md`, `../00_foundation/04_decision_rules.md`）
- V3 本体（→ `../90_archive/99_legacy_v3_pointer.md` 経由）
- V3 → V4 マッピング正本（→ `../00_foundation/09_v3_to_v4_mapping.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- V3 の資料を V4 正本として扱う記述が混入した
- V3 本体のテキストを大量コピーした

## 関連ファイル

- `source_pins.md` §3 — V3 の出典（repo / local path）
- `../90_archive/99_legacy_v3_pointer.md` — V3 への明示的 pointer
- `../00_foundation/09_v3_to_v4_mapping.md` — V3 → V4 マッピング（V4 正本）
