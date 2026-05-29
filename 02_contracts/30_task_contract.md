---
id: contract.task.v1
status: planned
owner: 02_contracts
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 30_task_contract.md — target repo ↔ CompanyOS UI の Task 連携契約

## 役割

target repo の Task を CompanyOS UI に渡すときの連携契約を後段で定義する。`00_contract_map.md` に `contract.task.v1` として planned 既出であり、本 file がそれを実体化する。

Task の業務正本は target repo 側に残し、UI には正規化された参照のみを渡す（正本コピー禁止）。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。MVP では `workflow_status` を Task status に流用しており、Task 専用の連携が必要になった段階で active 化する（`../03_status_metrics/20_task_status.md` 移行と同期）。

## 持つもの（後段で本格実装する内容）

- CompanyOS の `task_source_contract.yml` の `normalized_task_pointer` を ID 参照する方法
- UI に表示するフィールド / 表示しないフィールドの線引き
- Task → Surface 投影の境界（投影であって書き戻しではない）
- 正規化の責任分界点（後で追加する予定）

## 持たないもの

- Task の status enum 定義（→ `../03_status_metrics/20_task_status.md`）
- Task entity 定義本体（→ `../01_meaning_model/10_entities.md` §4）
- Surface 表現の詳細（→ `40_surface_contract.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- UI からの変更が Task 業務正本へ直接書き戻される契約になる

## 関連ファイル

- `00_contract_map.md`
- `40_surface_contract.md`
- `../01_meaning_model/10_entities.md`（§4 Task）
- `../03_status_metrics/20_task_status.md`
