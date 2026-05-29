---
id: feedback.quality.v1
status: planned
owner: 30_feedback
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# quality_feedback.md — 品質フィードバック集約入口

## 役割

`30_feedback/raw/` に蓄積された観測の中で **品質に関する FEV** を横断的に集約する入口。
`07_quality/` 配下の品質ゲート・critical gates・acceptance criteria・自己確認手順に関する観測を対象とする。
品質基準の過不足・ゲートの運用上の問題・チェック漏れパターンなどを集める。
判断・抽象化は行わず、raw からの集約 pointer を管理するだけ。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。品質関連の FEV が raw に複数件蓄積され、集約の必要性が生まれたタイミングで実装する。

## 持つもの（後段で本格実装する内容）

- `raw/{YYYY-MM}.md` から品質カテゴリ FEV への逆引きリンク
- 影響する quality ファイルへのポインタ（`../07_quality/`）
- 繰り返し出現している観測の列挙（判断なし）

## 持たないもの

- 判断・抽象化（→ `../31_learning/`）
- raw 本体（append は `raw/{YYYY-MM}.md` に行う）
- 品質基準の変更決定（→ 昇格プロセスを経ること）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 品質基準変更の判断がここに書かれる
- raw 本体がここに書かれる

## 関連ファイル

- `raw/{YYYY-MM}.md`
- `_index.md`
- `../07_quality/README.md` — quality root
- `../07_quality/30_critical_gates.md`
- `../31_learning/00_promotion_protocol.md`
