---
id: contract.templates.v1
status: planned
owner: 02_contracts
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# templates/ — contract 作成用テンプレ置き場

## 役割

新しい contract を起こすときにコピーして使う空枠テンプレートを集約する folder。各テンプレは section 構成だけを持ち、本文は持たない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 folder は MVP ではまだ使わない（active 化しない）。DRR（Decision Rule Review）通過後、新規 contract を起こす段階でコピー元として使う。MVP では既存 active contract を直接読む。

## このフォルダが持つもの

| file | 役割 | status |
| --- | --- | --- |
| `repo_contract_template.md` | repo_contract の新規作成雛形 | — 後段 |
| `workflow_contract_template.md` | workflow_contract の新規作成雛形 | — 後段 |
| `surface_contract_template.md` | surface_contract の新規作成雛形 | — 後段 |
| `sync_contract_template.md` | sync_contract の新規作成雛形 | — 後段 |

## このフォルダが持たないもの

- contract 本体（→ 各 `../NN_*_contract.md`）
- contract 一覧と方向（→ `../00_contract_map.md`）
- DRR 手続きの定義（→ `../../00_foundation/04_decision_rules.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- テンプレに具体 contract の本文が混入する（実例は各 contract file が正本）

## 関連ファイル

- `../00_contract_map.md`
- `../../00_foundation/04_decision_rules.md`（DRR）
