---
id: contract.template.surface.v1
status: planned
owner: 02_contracts
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# surface_contract_template.md — surface_contract 新規作成の雛形

## 役割

新しい surface_contract を起こすときにコピーして使う空枠テンプレート。後段では surface_contract の section 構成だけを空枠として持つ（本文は持たない）。

記入済みの実例は `../40_surface_contract.md`。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。新規 surface_contract を起こす必要が生じた段階でコピー元として使う。

## 持つもの（後段で本格実装する内容）

- Surface の対象正本・投影先の空枠 section
- 表示する / 表示しないフィールドの空枠 section
- 「Surface は正本ではない」明記欄の空枠 section
- 最低 acceptance / 止める条件の空枠 section
- 各 section の記入ガイド（後で追加する予定）

## 持たないもの

- 記入済みの contract 本文（→ 実例 `../40_surface_contract.md`）
- 他種別の contract 雛形（→ 同 folder の各 `*_template.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 雛形に特定 Surface の具体値が埋め込まれる（テンプレの汎用性喪失）

## 関連ファイル

- `../40_surface_contract.md`
- `README.md`
