---
id: workflow.youtube_video_production.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# youtube_video_production — YouTube 動画制作 workflow 型

## 役割

youtube_ops_repo が参照する、動画を企画から公開・分析まで回す workflow 型。台本・編集・公開の Phase 連続を定義する。本 file は型であり、台本・素材の正本は target repo 側に置く。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。youtube_ops_repo が実運用に入るときに本格詳細化する。

## 持つもの

- 動画制作の Phase 型（企画 → 台本 → 収録 → 編集 → 公開 → 分析）
- 入出力定義と公開準備 gate の骨格（型レベル）

## 持たないもの

- 台本・素材の正本（target repo 側）
- 動画個別の機密メモ

## 目的（後段で詳細化）

YouTube 動画を、企画 → 台本 → 収録 → 編集 → 公開 → 分析の一貫フローで制作し、進行 status を CompanyOS 上で可視化する。

## Phase の連続（概要・後段で詳細化）

企画 → 台本 → 収録 → 編集 → 公開 → 分析。各 Phase の詳細手順は後段で `../../02_contracts/20_workflow_contract.md` 準拠で記述する。

## 入出力（後段で詳細化）

- 入力：企画テーマ / 台本構成
- 出力：動画 meta / 台本 / 公開記録 / 分析メモ（target repo 側に正本）

## gate（任意・後段で詳細化）

- タイトル / サムネ / 台本 / 公開準備 の確認（後段で critical gate 化を検討）

## 関連 prompt・tool（後段で詳細化）

- 後段で確定（台本生成 Prompt を使う場合は prompt_repo を ID 参照）

## 関連 archetype

- `../repo/youtube_ops_repo.md`

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 台本・素材の正本を本 file に書き込む

## 関連ファイル

- `README.md`
- `../repo/youtube_ops_repo.md`
- `../../02_contracts/20_workflow_contract.md`
