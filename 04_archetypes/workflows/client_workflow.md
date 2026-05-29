---
id: workflow.client_workflow.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# client_workflow — クライアント案件 workflow 型

## 役割

client_repo が参照する、クライアント案件を標準フローで回す workflow 型。依頼受領から納品・振り返りまでの Phase 連続を定義する。本 file は型であり、案件ごとの正本は target repo 側の `10_clients/` に置く。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。client_repo が実運用に入るときに本格詳細化する。

## 持つもの

- クライアント案件の Phase 型（依頼 → 契約 → WBS → 制作・レビュー → 納品 → 振り返り）
- 入出力定義と承認・納品 gate の骨格（型レベル）

## 持たないもの

- 案件業務の正本・機密（target repo 側 `10_clients/`）
- 案件個別の実データ

## 目的（後段で詳細化）

クライアント案件を、依頼 → 契約 → WBS → 制作 → レビュー → 納品 → 振り返りの標準フローで回し、進行 status を CompanyOS 上で可視化する。

## Phase の連続（概要・後段で詳細化）

依頼受領 → 契約確認 → WBS 作成 → 制作・レビュー → 納品 → 振り返り。各 Phase の詳細手順は後段で `../../02_contracts/20_workflow_contract.md` 準拠で記述する。

## 入出力（後段で詳細化）

- 入力：依頼内容（brief）/ 契約条件 / 期限
- 出力：案件 meta / 納品記録 / 振り返り（target repo 側に正本）

## gate（任意・後段で詳細化）

- 承認・納品の状態が記録されているか（後段で critical gate 化を検討）

## 関連 prompt・tool（後段で詳細化）

- 後段で確定（automation_pack を使う場合の reminder など）

## 関連 archetype

- `../repo/client_repo.md`

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 案件業務正本・機密を本 file に書き込む

## 関連ファイル

- `README.md`
- `../repo/client_repo.md`
- `project_management.md`
- `../../02_contracts/20_workflow_contract.md`
