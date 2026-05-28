---
id: status_metric.readiness_scores.v1
status: planned
owner: 03_status_metrics
note: "住所と役割確保のための stub。本格実装は後段。score 概念のみ列挙。計算式・実装コードなし。"
---

# 60_readiness_scores.md — 準備スコア

## 役割

workflow / artifact が「次のフェーズに進める状態か」を表す **準備スコアの概念** を定義する。

`publish_ready` status（`10_workflow_status.md`）の根拠となる指標群を数値化・段階化することが目的。

**planned stub であり後段で本格実装する。** 計算式・実装コードは書かない。

## MVP での扱い

本 file は MVP では active 化しない。

`publish_ready` 判定は現状 `10_workflow_status.md` の enum で binary（yes/no）に扱われている。準備スコアの段階的可視化が必要になる段階で詳細化する。

`50_quality_scores.md` と並行して active 化を検討する。

## 持つもの

- 準備スコアの概念一覧（公開準備・実行準備・レビュー準備）
- 各スコアが測る内容の説明
- `publish_ready` status との関係

## 持たないもの

- 計算式・スコアリング実装
- 品質スコアの定義（→ `50_quality_scores.md`）
- gate 判定（→ `07_quality/30_critical_gates.md`）

---

## score 概念一覧（後段で確定）

後段で以下の概念を整理する（確定前につき仮称）：

- `publish_readiness` — 公開準備スコア。`publish_ready` status の根拠。必須 gate・品質閾値・承認状態を統合した値
- `execution_readiness` — 実行準備スコア。AI / human が次の Task を安全に実行できる状態かの指標
- `review_readiness` — レビュー準備スコア。人間レビュアーが判断するために必要な情報が揃っているかの指標

### `publish_ready` との関係

`10_workflow_status.md` の `publish_ready` status は「全 Task 完了、最終公開承認待ち」を意味する。

本 file active 化後は、`publish_readiness` スコアが閾値を超えた場合に `publish_ready` への遷移を推奨する仕組みとする（binary ではなく段階的判定）。

## 最低 acceptance

- 本 stub の存在意義が読める
- score 概念の一覧が読める
- `publish_ready` status との関係が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 計算式・実装をここに書く
- 品質スコア（`50_quality_scores.md`）との役割が混在する

## 関連ファイル

- `10_workflow_status.md`（`publish_ready` status の定義）
- `50_quality_scores.md`（品質スコアとの役割分担）
- `../07_quality/30_critical_gates.md`（gate の正本）
