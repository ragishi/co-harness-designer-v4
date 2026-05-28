---
id: quality.review_rubrics.v1
status: planned
owner: 07_quality
note: "住所と役割確保のための stub。本格実装は後段。"
---

# 50_review_rubrics.md — レビュー基準

## 役割

設計レビュー・実装レビュー時に、何をどう評価するかの rubric を定義する。`10_common_quality.md` + `30_critical_gates.md` の「満たすべき基準」を、「どう測るか」へ変換する。

**planned stub であり、後段で本格実装する。** MVP では critical gate pass / fail 確認が唯一の品質確認。本 stub は住所と役割の確保。

## MVP での扱い

本 file は MVP では active 化しない。MVP レビューは `30_critical_gates.md` の pass / fail チェックで代替する。rubric の体系化は実レビュー経験が積まれた後段で行う。関連既存 file: `10_common_quality.md` / `30_critical_gates.md`。

## 後段で持つ内容（概要）

- **設計レビュー rubric**: 目的・構造・DRR 通過・tier 配置の評価軸
- **実装レビュー rubric**: common quality 9 項目の具体確認手順・MNP gate 確認
- **採点方式**: pass / fail（critical）vs スコア 1-5（advisory）の使い分け定義
- **レビュー対象の分類**: self-review / peer-review / gate-runner の 3 段
- **rubric バージョン管理**: どの rubric で評価したかの記録方法

## 採点方式（planned、後段で詳細化）

```text
critical gate: pass / fail（1 つでも fail で止まる）
advisory gate: warning（記録するが止めない）
rubric score: 後段で設計（1-5 スコア or pass/warn/fail の 3 段）
```

## 持つもの

- critical / advisory の採点方式の方向性
- 後段で詳細化する rubric 軸の概要
- 既存 gate との関係定義

## 持たないもの

- gate の本文（→ `30_critical_gates.md` / `40_advisory_gates.md`）
- 採点実装コード
- 採点結果の保存先実装

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- gate の本文を本ファイルに重複して書く
- rubric スコアの実装コードを書き始める

## 関連ファイル

- `10_common_quality.md`
- `30_critical_gates.md`
- `40_advisory_gates.md`（planned）
- `00_quality_map.md`（planned）
- `../CLAUDE.gate.md`
