---
id: status_metric.quality_scores.v1
status: planned
owner: 03_status_metrics
note: "住所と役割確保のための stub。本格実装は後段。score 概念のみ列挙。計算式・実装コードなし。"
---

# 50_quality_scores.md — 品質スコア

## 役割

V4 が産む target repo の成果物・workflow が「どれだけ品質基準を満たしているか」を数値または段階で表す **品質スコアの概念** を定義する。

gate 判定（pass/fail）ではなく、継続的な品質可視化のための指標。

**planned stub であり後段で本格実装する。** 計算式・実装コードは書かない。

## MVP での扱い

本 file は MVP では active 化しない。

品質スコアは `07_quality/30_critical_gates.md` の gate を通過した後、継続モニタリングが必要になる段階で詳細化する。

## 持つもの

- 品質スコアの概念一覧
- 各スコアが何を測るかの説明
- `07_quality/` との役割分担の整理

## 持たないもの

- 計算式・スコアリング実装
- gate pass/fail 判定（→ `07_quality/30_critical_gates.md`）
- UI 表示ロジック

---

## score 概念一覧（後段で確定）

後段で以下の概念を整理する（確定前につき仮称）：

- `coverage` — 必須フィールド・セクションの充足率
- `clarity` — 記述の明確さ（曖昧語・未定義語の比率など）
- `source_alignment` — source_pin との整合度（generated が正本から乖離していないか）
- `ssot_compliance` — SSOT ルール（重複定義・相互参照の健全性）への準拠度
- `gate_history` — 過去の gate 通過率・失敗傾向

各スコアの計算式・閾値は本 file active 化時に `07_quality/` と整合させて定義する。

## 最低 acceptance

- 本 stub の存在意義が読める
- score 概念の一覧が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 計算式・実装をここに書く
- gate 判定をここに書く（`07_quality/` の責務）

## 関連ファイル

- `60_readiness_scores.md`（準備スコアとの役割分担）
- `../07_quality/30_critical_gates.md`（gate 判定の正本）
- `../07_quality/10_common_quality.md`
