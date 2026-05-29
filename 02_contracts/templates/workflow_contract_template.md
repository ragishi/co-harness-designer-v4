---
id: contract.template.workflow.v1
status: planned
owner: 02_contracts
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# workflow_contract_template.md — workflow_contract 新規作成の雛形

## 役割

新しい workflow_contract を起こすときにコピーして使う空枠テンプレート。後段では workflow_contract の section 構成だけを空枠として持つ（本文は持たない）。

記入済みの実例は `../20_workflow_contract.md`。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。新規 workflow_contract を起こす必要が生じた段階でコピー元として使う。

## 持つもの（後段で本格実装する内容）

- workflow の目的・適用範囲の空枠 section
- Phase 連続と入出力の空枠 section
- gate（任意）の空枠 section
- 最低 acceptance / 止める条件の空枠 section
- 各 section の記入ガイド（後で追加する予定）

## 持たないもの

- 記入済みの contract 本文（→ 実例 `../20_workflow_contract.md`）
- 他種別の contract 雛形（→ 同 folder の各 `*_template.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 雛形に特定 workflow の具体手順が埋め込まれる（テンプレの汎用性喪失）

## 関連ファイル

- `../20_workflow_contract.md`
- `README.md`
