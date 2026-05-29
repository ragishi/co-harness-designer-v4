---
id: feedback.repo_design.v1
status: planned
owner: 30_feedback
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# repo_design_feedback.md — repo 設計フィードバック集約入口

## 役割

`30_feedback/raw/` に蓄積された観測の中で **repo 設計全般に関する FEV** を横断的に集約する入口。
root 構造・ディレクトリ設計・SSOT 方針・ファイル命名規則など、V4 設計の骨格に影響する観測を対象とする。
raw を集めることが目的であり、ここで判断・抽象化は行わない。
後段の `../31_learning/` への昇格判断はこのファイルの外で行う。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。raw に repo 設計関連の FEV が複数件蓄積され、集約の必要性が生まれたタイミングで実装する。

## 持つもの（後段で本格実装する内容）

- `raw/{YYYY-MM}.md` から repo 設計カテゴリ FEV への逆引きリンク
- カテゴリ別の件数サマリ（集約のみ、本文は raw に残す）
- 繰り返し出現している観測の列挙（判断なし、raw pointer のみ）

## 持たないもの

- 判断・抽象化（→ `../31_learning/`）
- raw 本体（append は `raw/{YYYY-MM}.md` に行う）
- カテゴリ外の観測（ui / contract / archetype / build / quality は各専用ファイルへ）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 判断・抽象化がこのファイルに混入する
- raw 本体がここに書かれる

## 関連ファイル

- `raw/{YYYY-MM}.md` — raw 観測の本体
- `_index.md`
- `../31_learning/signals/` — 昇格後の兆候置き場
- `../31_learning/00_promotion_protocol.md`
