---
id: extension.installed.analytics_ops.v1
status: planned
owner: 40_extensions
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# analytics_ops/ — 公開後 KPI 計測 extension

## 役割

公開されたコンテンツの **KPI 計測・分析・レポーティング** を提供する extension。
公開後の閲覧数・エンゲージメント・コンバージョンなどの指標を追跡し、次のコンテンツ戦略に活かすためのデータ整理ワークフローを担う。
推奨 `depends_on`（必須ではない）。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
KPI 計測を必要とする archetype が `depends_on: analytics_ops` を宣言し、admission_criteria を満たしたタイミングで本格実装する。

## このフォルダが持つもの（後段で本格実装する内容）

- KPI 定義・指標一覧（メディアタイプ別）
- 定期レポートテンプレート
- データ収集ワークフロー（手動・自動）
- 改善サイクル（計測 → 分析 → 次回反映）の定義

## このフォルダが持たないもの

- 公開処理（→ `../publish_pipeline/`）
- 広告・マネタイズ戦略（→ 各 archetype 固有）
- archetype 定義（→ `../../../04_archetypes/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 計測ロジックが特定 archetype に強く結合した（汎用性喪失）
- extension が archetype を参照し始めた（一方向ルール違反）

## 関連ファイル

- `../publish_pipeline/` — 公開処理
- `../README.md` — installed 全体
- `../../00_extension_policy.md` — 一方向依存ルール
