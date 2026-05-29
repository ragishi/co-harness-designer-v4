---
id: workflow.research_to_content.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# research_to_content — リサーチ起点の記事化 workflow 型

## 役割

note_production_repo（active archetype）が参照する、リサーチ素材を起点に記事化する workflow 型。情報収集から記事 draft へ落とす Phase 連続を定義する。本 file は型であり、リサーチ素材・記事本文の正本は target repo 側に置く。active archetype が宣言する `workflow.research_to_content.v1` と整合させる。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。note_production_repo の実運用でリサーチ起点の記事化が必要になったときに本格詳細化する。型の id は active archetype の記述と一致させる。

## 持つもの

- リサーチ起点の記事化 Phase 型（収集 → 出典整理 → 要点抽出 → 構成案 → draft 連携）
- note_article_production への連携点
- 出典追跡 gate の骨格（型レベル）

## 持たないもの

- リサーチ素材・記事本文の正本（target repo 側）
- note_article_production と重複する執筆 Phase の正本

## 目的（後段で詳細化）

リサーチで集めた情報を整理・構造化し、note_article_production に渡せる記事 draft の起点を作る。出典管理と要点抽出を一貫フローで回す。

## Phase の連続（概要・後段で詳細化）

リサーチ収集 → 出典整理 → 要点抽出 → 構成案 → draft 連携（note_article_production へ）。各 Phase の詳細手順は後段で `../../02_contracts/20_workflow_contract.md` 準拠で記述する。

## 入出力（後段で詳細化）

- 入力：リサーチテーマ / 収集した情報源
- 出力：出典リスト / 要点メモ / 構成案（note_article_production の入力になる、正本は target repo 側）

## gate（任意・後段で詳細化）

- 出典が記録され引用が追跡可能か（後段で critical gate 化を検討）

## 関連 prompt・tool（後段で詳細化）

- 後段で確定（要点抽出 Prompt を使う場合は prompt_repo を ID 参照）

## 関連 archetype

- `../repo/note_production_repo.md`

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- active な note_production_repo が参照する型として整合している
- note_article_production への連携点が読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- リサーチ素材・記事本文の正本を本 file に書き込む

## 関連ファイル

- `README.md`
- `../repo/note_production_repo.md`
- `note_article_production.md`
- `../../02_contracts/20_workflow_contract.md`
