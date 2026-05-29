---
id: extension.installed.publish_pipeline.v1
status: planned
owner: 40_extensions
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# publish_pipeline/ — 公開準備・公開後フォロー extension

## 役割

コンテンツの**公開準備・公開実行・公開後フォロー**のワークフローを提供する extension。
note / YouTube / SNS など、公開処理を持つ owner 系 archetype が `depends_on` する想定。
`content_production/` が制作 core を担い、本 extension が公開フェーズを担う。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
公開処理を持つ archetype が `depends_on: publish_pipeline` を宣言し、admission_criteria を満たしたタイミングで本格実装する。

## このフォルダが持つもの（後段で本格実装する内容）

- 公開チェックリスト・公開前レビュー手順
- 公開実行ログ・スケジュール管理テンプレート
- 公開後フォロー（初速確認、読者対応、更新判断）の定義
- 公開ステータス enum

## このフォルダが持たないもの

- 制作フロー（→ `../content_production/`）
- KPI 計測・分析（→ `../analytics_ops/`）
- archetype 定義（→ `../../../04_archetypes/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 制作フローと公開フローの境界が曖昧になった
- extension が archetype を参照し始めた（一方向ルール違反）

## 関連ファイル

- `../content_production/` — 制作 core
- `../analytics_ops/` — 公開後 KPI
- `../../00_extension_policy.md` — 一方向依存ルール
- `../README.md` — installed 全体
