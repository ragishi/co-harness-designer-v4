---
id: archetype.youtube_ops_repo.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# youtube_ops_repo — YouTube 動画制作運用の archetype

## 役割

YouTube 動画を、企画・台本・収録・編集・公開・分析まで一貫して管理する target repo の archetype（owner_repo 系の制作運用）。note_production_repo の動画版にあたり、媒体特性（サムネ / 尺 / チャンネル KPI）を持つ。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。YouTube 制作専用の target repo を起こす需要が観測され、DRR 5 質問を通過したときに本格詳細化する。

## 持つもの

- 動画制作の SSOT（企画 / 台本 / 収録 / 編集 / 公開 / 分析 のループ）
- 媒体固有要素（サムネ / 尺 / チャンネル KPI）
- 必須 / 推奨 / 禁止 module 構成（下記で詳細化）
- youtube_video_production workflow への参照

## 持たないもの

- 台本本文・編集素材の正本（target repo 側 / `.companyos/` には置かない）
- client 概念（受託案件は別 repo）
- 制作運用と無関係な module（client_ops 等）

## 目的（後段で詳細化）

動画制作の **企画 → 台本 → 収録 → 編集 → 公開 → 分析** を一貫した SSOT として管理する。CompanyOS UI 上で動画カード・公開準備・チャンネル指標を表示する。

## 必須 module（後段で詳細化）

- `content_production` — 動画制作の core ループ
- `publish_pipeline` — 公開準備・公開後フォロー
- `feedback_loop`（built-in、Common Core）

## 推奨 module（後段で詳細化）

- `analytics_ops` — 再生数 / 登録者 / 視聴維持率の KPI 追跡

## 禁止 module（後段で詳細化）

- `client_ops` — 制作 repo は client 概念を持たない（受託案件は別 repo に分離）

## 持つべき workflow（後段で詳細化）

- `workflow.youtube_video_production.v1` — 企画から公開・分析まで

## CompanyOS に表示するもの（後段で詳細化）

- 動画カード（タイトル / 進行 status / owner / next_action）
- 公開準備状態
- source_path（動画 meta への参照）

## CompanyOS に表示しないもの（後段で詳細化）

- 台本本文・編集中素材の正本
- 未公開の機密メモ

## archetype 固有の root（後段で詳細化）

Common Core 9 entries（`../../02_contracts/10_repo_contract.md` 参照）に加え、`02_workflows/` と素材・台本フォルダを持つ見込み。具体構造は後段で確定する。

## quality_profile（後段で詳細化）

- common quality: 全部適用（`../../07_quality/10_common_quality.md`）
- archetype quality（後段）：タイトル / サムネ / 台本 / 公開準備 の critical gate

## 関連 contract（後段で詳細化）

- `contract.repo.v1` — Common Core 遵守
- `contract.surface.v1` — 動画カード / workflow lens
- `contract.workflow.v1` — youtube_video_production の書き方

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- note_production_repo との媒体差（動画固有要素）が読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 台本本文を `.companyos/` 内に置く前提を書く（surface_contract 違反）

## 関連ファイル

- `README.md`
- `note_production_repo.md`
- `../00_archetype_framework.md`
- `../workflows/youtube_video_production.md`
- `../../02_contracts/40_surface_contract.md`
