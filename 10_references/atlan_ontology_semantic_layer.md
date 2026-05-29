---
id: reference.atlan_ontology_semantic_layer.v1
status: planned
owner: 10_references
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# atlan_ontology_semantic_layer.md — Atlan 記事の深掘りノート

## 役割

Atlan 記事「Ontology vs. Semantic Layer」の深掘りメモを置く場所です。記事の出典管理は `source_pins.md` §1 に委譲しており、本 file は詳細な読み込みメモ・V4 への示唆・引用の整理を後段で行う場所として住所を確保します。**本 file は V4 の正本ではありません**。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`01_meaning_model/` や `03_status_metrics/` の設計検討が深まり、Atlan 記事の詳細参照が必要になった段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- Atlan 記事の要点メモ（ontology / semantic layer / context layer / SSOT 分離の整理）
- 記事のどの部分が V4 設計のどこに影響したかの対応表
- V4 正本と記事の間で概念をどう読み替えたかのメモ
- 記事中で V4 が採用しなかった部分とその理由

## 持たないもの

- 出典表（URL / 取得日 / publisher）→ `source_pins.md` §1 を参照
- V4 の正本（→ `../01_meaning_model/`, `../03_status_metrics/`, `../00_foundation/01_principles.md`）
- 記事本体の大量コピー（リンクと要点のみ）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 出典を `source_pins.md` に記録せず本 file にのみ記載した
- 参考元を V4 正本として扱う記述が混入した

## 関連ファイル

- `source_pins.md` §1 — Atlan 記事の出典（URL / 取得日 / publisher）
- `../01_meaning_model/` — ontology 相当（V4 では「意味モデル」）
- `../03_status_metrics/` — semantic layer 相当（V4 では「状態・指標」）
- `../05_read_sets/` — context layer 相当（V4 では「読書セット」）
