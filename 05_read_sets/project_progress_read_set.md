---
id: read_set.project_progress.v1
status: planned
owner: 05_read_sets
target_archetypes:
  - project_progress_repo
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# project_progress_read_set.md — project 管理 repo 設計時の読書セット

## 役割

`project_progress_repo` archetype を持つ target repo を設計・scaffold・レビューするとき、AI が読むべき file セットと順番を定義する。
プロジェクト進捗管理・マイルストーン追跡・チーム分担に固有の contract・metric を優先して読む順番を後段で確定させる。
`companyos_repo_design_read_set.md`（共通入口）から本 read_set へ移行する際の受け皿として機能する。
pointer-only であり、entity / contract / metric の本文は持たない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。
active 化の契機: `04_archetypes/repo/project_progress_repo.md` が active 化されたとき。

## 持つもの（後段で本格実装する内容）

- 読む順番（`project_progress_repo` 固有の file pointer リスト）
- 読まないもの（他 archetype の定義・無関係な root）
- 想定する作業（project 管理 repo の scaffold / レビュー / status 変換設定）
- 本 archetype 固有の注意事項（例: マイルストーン status 管理、`blocked` 状態の伝播ルール）

## 持たないもの

- entity / contract の定義本体（→ `../01_meaning_model/`, `../02_contracts/`）
- archetype 定義（→ `../04_archetypes/repo/project_progress_repo.md`）
- 他 archetype の read_set（→ 各 `*_read_set.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- entity / contract の本文を直書きする
- `project_progress_repo` 以外の archetype 向け内容を混入する

## 関連ファイル

- `README.md`（この root の入口）
- `00_read_set_policy.md`（read_set 共通方針）
- `companyos_repo_design_read_set.md`（共通入口、archetype 選定前に読む）
- `../04_archetypes/repo/project_progress_repo.md`（対応 archetype 定義）
- `../03_status_metrics/10_workflow_status.md`（status enum 正本）
