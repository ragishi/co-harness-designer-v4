---
id: workflow.sns_post_production.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# sns_post_production — SNS 投稿制作 workflow 型

## 役割

sns_operations_repo が参照する、SNS 投稿を企画から投稿・反応分析まで回す workflow 型。短サイクル・高頻度の Phase 連続を定義する。本 file は型であり、投稿本文の正本は target repo 側に置く。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。sns_operations_repo が実運用に入るときに本格詳細化する。

## 持つもの

- SNS 投稿制作の Phase 型（企画 → 作成 → 予約 → 投稿 → 反応分析）
- 入出力定義と投稿 gate の骨格（型レベル）

## 持たないもの

- 投稿本文の正本（target repo 側）
- 媒体アカウント認証情報

## 目的（後段で詳細化）

SNS 投稿を、企画 → 作成 → 予約 → 投稿 → 反応分析の一貫フローで制作し、投稿状態を CompanyOS 上で可視化する。

## Phase の連続（概要・後段で詳細化）

企画 → 作成 → 予約 → 投稿 → 反応分析。各 Phase の詳細手順は後段で `../../02_contracts/20_workflow_contract.md` 準拠で記述する。媒体別制約（文字数・形式）の差は後段で扱う。

## 入出力（後段で詳細化）

- 入力：投稿テーマ / 媒体 / 予定投稿日
- 出力：投稿 meta / 投稿本文 / 反応メモ（target repo 側に正本）

## gate（任意・後段で詳細化）

- 投稿文 / 媒体別制約 / 予約日 の確認（後段で critical gate 化を検討）

## 関連 prompt・tool（後段で詳細化）

- 後段で確定（投稿文生成 Prompt を使う場合は prompt_repo を ID 参照）

## 関連 archetype

- `../repo/sns_operations_repo.md`

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 投稿本文の正本を本 file に書き込む

## 関連ファイル

- `README.md`
- `../repo/sns_operations_repo.md`
- `../../02_contracts/20_workflow_contract.md`
