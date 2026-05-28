---
id: quality.drift_checks.v1
status: planned
owner: 07_quality
note: "住所と役割確保のための stub。本格実装は後段。"
---

# 70_drift_checks.md — 複雑化・ズレ検出

## 役割

V4 repo 自身と target repo が、時間の経過とともに設計意図からズレていく（複雑化・用語 drift・DRR 未通過追加）を検出する機構の定義場所。

**planned stub であり、後段で本格実装する。** MVP では DRR 5 質問の手動実行が唯一のズレ検出手段。本 stub は住所と役割の確保。

## MVP での扱い

本 file は MVP では active 化しない。MVP での drift check は `../00_foundation/04_decision_rules.md` の DRR 5 質問を手動で実行することで代替する。本 stub は後段で自動・半自動のチェック機構を追加する際の器として機能する。

> **現時点の正本 pointer:** `../00_foundation/04_decision_rules.md` → DRR 5 questions

---

## 検出対象（後段で詳細化）

後段で以下の drift パターンを検出する機構を設計する予定:

1. **root 数増減 drift**: 宣言された root 数から増減していないか
2. **用語 drift**: ファイル間で同じ概念に異なる名前が使われていないか
3. **tier 混在 drift**: `01_process/` に基準が、`02_quality_standards/` にフローが入っていないか（V3 の 5-tier 思想継承）
4. **contract 抜け drift**: 必須 contract が存在しないまま実装が進んでいないか
5. **MVP boundary drift**: MVP 外の実装が DRR なしで追加されていないか

## DRR 5 質問（現行の手動チェック、正本は 00_foundation/04_decision_rules.md）

本 stub が active 化するまで、以下は手動で確認する:

```text
1. このエントリがなければ既存の何かが壊れるか？
2. 既存の root / contract / archetype で代替できないか？
3. 追加後 1 年使い続けるか？
4. 他の AI が迷わず分類できるか？
5. 追加コストは使用価値を上回るか？
```

## 後段で持つ内容（概要）

- drift パターン別の自動検出 script pointer
- 手動チェック補助テンプレート（session 開始時に使う）
- drift 発見時の記録先と escalation 手順
- drift が N 回再発した場合の `31_learning/` 昇格条件

## 持つもの

- drift パターンの分類（概要）
- DRR 5 質問の pointer
- 後段で詳細化する内容の概要

## 持たないもの

- DRR の本文（→ `../00_foundation/04_decision_rules.md`）
- drift 検出の実装コード
- critical gate の判定（→ `30_critical_gates.md` の DRR Gate）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- DRR の本文をここに重複して書く
- drift 検出の実装コードを書き始める

## 関連ファイル

- `../00_foundation/04_decision_rules.md`（DRR 5 questions 正本）
- `30_critical_gates.md`（DRR Gate を含む）
- `../30_feedback/raw/`（drift 発見の記録先）
- `../31_learning/`（昇格先）
- `00_quality_map.md`（planned）
