---
id: workflow.note_article_production.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# note_article_production — note 記事制作 workflow 型

## 役割

note_production_repo（active archetype）が参照する、記事を企画から公開・学習まで回す workflow 型。本 file は型であり、記事本文の正本は target repo 側の `20_workspace/` / `21_outputs/` に置く。active archetype が宣言する `workflow.note_article_production.v1` と整合させる。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。note_production_repo の Phase 3 実運用が始まるときに本格詳細化する。型の id・Phase 骨格は active archetype の記述（企画 → 執筆 → レビュー → 公開 → 学習）と一致させる。

## 持つもの

- 記事制作の Phase 型（企画 → 執筆 → レビュー → 公開 → 学習）
- 入出力定義と gate の骨格（型レベル）
- note_production_repo が参照する id 整合

## 持たないもの

- 記事本文の正本（target repo 側 `20_workspace/` / `21_outputs/`）
- note_production_repo の Phase 記述と矛盾する独自 Phase

## 目的（後段で詳細化）

note 記事を、企画 → 執筆 → レビュー → 公開 → 学習の一貫フローで制作し、進行 status を CompanyOS 上で可視化する。

## Phase の連続（概要・後段で詳細化）

企画 → 執筆 → レビュー → 公開 → 学習。各 Phase の詳細手順は後段で `../../02_contracts/20_workflow_contract.md` 準拠で記述する。note_production_repo の section と齟齬を起こさないこと。

## 入出力（後段で詳細化）

- 入力：企画テーマ / 構成メモ
- 出力：記事 meta / 本文 draft / 公開記録 / 学習メモ（target repo 側に正本）

## gate（任意・後段で詳細化）

- タイトル / 本文 / 導入 / CTA / 公開準備 の確認（note_production_repo の archetype quality と対応、後段で詳細化）

## 関連 prompt・tool（後段で詳細化）

- 後段で確定（Prompt を使う場合は prompt_repo を ID 参照、本文は複製しない）

## 関連 archetype

- `../repo/note_production_repo.md`

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- active な note_production_repo が参照する型として整合している

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- note_production_repo の Phase 記述と矛盾する Phase を書く
- 記事本文の正本を本 file に書き込む

## 関連ファイル

- `README.md`
- `../repo/note_production_repo.md`
- `research_to_content.md`
- `../../02_contracts/20_workflow_contract.md`
