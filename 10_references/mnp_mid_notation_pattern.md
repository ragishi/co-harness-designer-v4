---
id: reference.mnp_mid_notation_pattern.v1
status: planned
owner: 10_references
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# mnp_mid_notation_pattern.md — MNP 記事の深掘りノート

## 役割

MNP（中間記法パターン）note 記事の深掘りメモを置く場所です。記事の出典管理は `source_pins.md` §2 に委譲しており、本 file は詳細な読み込みメモ・V4 への示唆・採用範囲の整理を後段で行う場所として住所を確保します。**本 file は V4 の正本ではありません**。

> 重要: V4 では MNP は Surface 用 optional extension に限定しています。root 化禁止 / 業務正本化禁止。この制約は本 file の後段実装時も変わりません。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`40_extensions/proposals/mnp_surface_pack/` の検討が進み、MNP 記事の詳細参照が必要になった段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- MNP 記事の要点メモ（DSL / parser / serializer / system prompt の 4 要素構造）
- V4 が MNP を Surface 用 optional extension に限定した理由の整理
- 「業務正本を MNP に入れない」原則の記事との対応
- 採用した部分・採用しなかった部分の対応表

## 持たないもの

- 出典表（URL / 取得日 / author）→ `source_pins.md` §2 を参照
- MNP の V4 内正本（→ `../02_contracts/80_mnp_surface_contract.md`）
- MNP exporter 仕様（→ `../06_build/exporters/mnp_surface_exporter.md`）
- 記事本体の大量コピー（リンクと要点のみ）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- MNP を V4 root として扱う記述が混入した
- 出典を `source_pins.md` に記録せず本 file にのみ記載した

## 関連ファイル

- `source_pins.md` §2 — MNP 記事の出典（URL / 取得日 / author）
- `../02_contracts/80_mnp_surface_contract.md` — MNP 使用条件契約（V4 正本）
- `../40_extensions/proposals/mnp_surface_pack/` — proposal pack
