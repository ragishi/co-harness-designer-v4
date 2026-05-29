---
id: workflow.project_management.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# project_management — 進捗管理 workflow 型

## 役割

project_progress_repo / client_repo が参照する、WBS と milestone を運用する workflow 型。タスク分解・進捗更新・milestone 達成判定の Phase 連続を定義する。本 file は型であり、実運用の WBS 正本は target repo 側に置く。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。project_management module を持つ archetype が実運用に入るときに本格詳細化する。

## 持つもの

- 進捗運用の Phase 型（WBS 作成 → 進捗更新 → milestone 判定 → 遅延対応 → 完了）
- 入出力定義と WBS gate の骨格（型レベル）

## 持たないもの

- WBS の実運用正本（target repo 側）
- プロジェクト個別の業務データ

## 目的（後段で詳細化）

WBS を立て、進捗を更新し、milestone の達成を判定して次アクションを導く。CompanyOS 上で進捗を可視化できる状態を維持する。

## Phase の連続（概要・後段で詳細化）

WBS 作成 → タスク着手・進捗更新 → milestone 判定 → 遅延対応 → 完了・振り返り。各 Phase の詳細手順は後段で `../../02_contracts/20_workflow_contract.md` 準拠で記述する。

## 入出力（後段で詳細化）

- 入力：プロジェクト目標 / 期限 / 担当者
- 出力：WBS meta / 進捗ログ / milestone 状態（target repo 側に正本）

## gate（任意・後段で詳細化）

- WBS に依存関係・期限・担当者が揃っているか（後段で critical gate 化を検討）

## 関連 prompt・tool（後段で詳細化）

- 後段で確定（automation_pack を使う場合の status 集計など）

## 関連 archetype

- `../repo/project_progress_repo.md`
- `../repo/client_repo.md`

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- WBS 業務正本を本 file に書き込む

## 関連ファイル

- `README.md`
- `../repo/project_progress_repo.md`
- `../../02_contracts/20_workflow_contract.md`
