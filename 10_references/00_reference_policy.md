---
id: reference.policy.v1
status: planned
owner: 10_references
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 00_reference_policy.md — 外部参考の扱い方針

## 役割

V4 が外部資料を参照する際のルールを定義します。参考元は V4 の正本ではなく、あくまで設計の参考として扱います。参考元と V4 正本が矛盾した場合は V4 正本を優先します。全参考元には出典（URL / 取得日 / author）が必須であり、`source_pins.md` がそのインデックスです。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`10_references/` 内の参考 file が実際に増えて運用が始まった段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- 外部参考を扱う際の原則（正本でない / 矛盾時 V4 優先 / 出典必須）
- 参考元の受け入れ基準（どんな資料を参考元として登録するか）
- 出典フォーマット（URL / 取得日 / author / publisher）の標準形
- `source_pins.md` との役割分担（policy はルール、source_pins は出典データ）
- 参考元の更新・廃止手続き

## 持たないもの

- 参考元本体（外部資料のコピー）
- 各参考元の詳細ノート（→ `atlan_ontology_semantic_layer.md`, `mnp_mid_notation_pattern.md` 等）
- 出典データ自体（→ `source_pins.md` の各 §）
- V4 正本（→ `../00_foundation/01_principles.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- V4 正本（`00_foundation/` 〜 `07_quality/`）と矛盾するポリシー案が混入した

## 関連ファイル

- `source_pins.md` — 外部参考の出典記録（4 主要参考元のインデックス）
- `README.md` — 10_references root の説明
- `../00_foundation/01_principles.md` — V4 正本の判断軸（P0–P5）
