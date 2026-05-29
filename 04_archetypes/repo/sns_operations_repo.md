---
id: archetype.sns_operations_repo.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# sns_operations_repo — SNS 投稿運用の archetype

## 役割

SNS 投稿（X / Instagram など）を、企画・作成・予約・投稿・反応分析まで一貫して管理する target repo の archetype。短サイクル・高頻度の投稿運用に最適化し、媒体横断のスケジュールと反応を扱う。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。SNS 運用専用の target repo を起こす需要が観測され、DRR 5 質問を通過したときに本格詳細化する。

## 持つもの

- SNS 投稿の SSOT（企画 → 作成 → 予約 → 投稿 → 反応分析）
- 投稿カレンダー / 反応指標
- 必須 / 推奨 / 禁止 module 構成（下記で詳細化）
- sns_post_production workflow への参照

## 持たないもの

- 投稿本文の正本・未公開 draft を `.companyos/` に置くこと
- アカウント認証情報
- client 概念（受託運用は別 repo）

## 目的（後段で詳細化）

SNS 投稿の **企画 → 作成 → 予約 → 投稿 → 反応分析** を一貫した SSOT として管理する。CompanyOS UI 上で投稿カード・投稿カレンダー・反応指標を表示する。

## 必須 module（後段で詳細化）

- `content_production` — 投稿制作の core ループ
- `publish_pipeline` — 投稿準備・投稿後フォロー
- `feedback_loop`（built-in、Common Core）

## 推奨 module（後段で詳細化）

- `analytics_ops` — インプレッション / エンゲージメント / フォロワー増減の KPI 追跡

## 禁止 module（後段で詳細化）

- `client_ops` — 投稿運用 repo は client 概念を持たない（受託運用は別 repo に分離）

## 持つべき workflow（後段で詳細化）

- `workflow.sns_post_production.v1` — 企画から投稿・反応分析まで

## CompanyOS に表示するもの（後段で詳細化）

- 投稿カード（媒体 / 進行 status / 予定投稿日 / next_action）
- 投稿カレンダー
- source_path（投稿 meta への参照）

## CompanyOS に表示しないもの（後段で詳細化）

- 投稿本文の正本・未公開 draft
- アカウント認証情報

## archetype 固有の root（後段で詳細化）

Common Core 9 entries（`../../02_contracts/10_repo_contract.md` 参照）に加え、`02_workflows/` と投稿カレンダー用フォルダを持つ見込み。具体構造は後段で確定する。

## quality_profile（後段で詳細化）

- common quality: 全部適用（`../../07_quality/10_common_quality.md`）
- archetype quality（後段）：投稿文 / 媒体別制約 / 予約日 の critical gate

## 関連 contract（後段で詳細化）

- `contract.repo.v1` — Common Core 遵守
- `contract.surface.v1` — 投稿カード / カレンダー lens
- `contract.workflow.v1` — sns_post_production の書き方

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- note / youtube との運用サイクル差（高頻度・短文）が読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 投稿本文を `.companyos/` 内に置く前提を書く（surface_contract 違反）

## 関連ファイル

- `README.md`
- `note_production_repo.md`
- `../00_archetype_framework.md`
- `../workflows/sns_post_production.md`
- `../../02_contracts/40_surface_contract.md`
