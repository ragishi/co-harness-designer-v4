---
id: foundation.v3_to_v4_mapping.v1
status: planned
owner: 00_foundation
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 09_v3_to_v4_mapping.md — V3 構造 → V4 構造の対応表

## 役割

V3（co-harness-design-v3）の構造が V4 のどの root に対応するかを後段で対応表化する。V3 を知る人間・AI が V4 を読むときの橋渡しと、なぜ V4 が構造を変えたのかの説明責任を果たす。

V3 本体はコピーしない。pointer のみを置く（local path: `/Users/saku/co-harness-design-v3/`）。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。V3 からの移行を実際に説明する必要が生じた段階、または V4 構造の確定後に対応表を埋める。

## 持つもの（後段で本格実装する内容）

- V3 の 5-tier core が V4 のどの root に対応するかの対応表
- 30_feedback / 31_learning の番号を V4 が継承した理由（V3 連続性）
- V4 が V3 から変えた点とその意図（archetype 中核化、contracts 統合、read_sets 採用 等）
- V3 用語 → V4 用語の差分（後で追加する予定）

## 持たないもの

- V3 本体の内容コピー（→ pointer `/Users/saku/co-harness-design-v3/`、`../90_archive/99_legacy_v3_pointer.md`）
- 外部参考 pin の管理（→ `../10_references/source_pins.md` §3 V3）
- V4 の設計原則本体（→ `01_principles.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- V3 本体の内容をここにコピーし始める（pointer 原則の違反）

## 関連ファイル

- `../90_archive/99_legacy_v3_pointer.md`
- `../10_references/source_pins.md`（§3 V3）
- `01_principles.md`
