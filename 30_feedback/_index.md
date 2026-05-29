---
id: feedback.index.v1
status: planned
owner: 30_feedback
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# _index.md — raw とカテゴリの navigate 入口

## 役割

`30_feedback/` 全体を横断する **navigate 索引**。
raw 月次ファイルへのポインタと 6 つのカテゴリ集約ファイルへのポインタを一覧化する。
読者が「どの raw に何があるか」「どのカテゴリに集めたか」を素早く把握できるように設計する。
判断・抽象化は一切行わず、記録の在処を示すだけの純粋な navigate 層。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。raw が複数月に増えてカテゴリ集約が本格稼働したタイミングで実装する。

## 持つもの（後段で本格実装する内容）

- `raw/{YYYY-MM}.md` への月別ポインタ一覧（FEV 件数サマリ付き）
- 6 カテゴリ集約ファイルへのポインタ（`repo_design_feedback.md` 等）
- 各 tier `feedback.md` の一覧（`00_foundation/feedback.md` 等）
- 最終更新日

## 持たないもの

- raw 本体（→ `raw/{YYYY-MM}.md`）
- 判断・抽象化（→ `../31_learning/_index.md`）
- カテゴリ集約の本文（→ 各 `*_feedback.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- raw の内容や判断結果がこのファイルに混入する

## 関連ファイル

- `README.md`
- `raw/`
- `repo_design_feedback.md`
- `ui_feedback.md`
- `contract_feedback.md`
- `archetype_feedback.md`
- `build_feedback.md`
- `quality_feedback.md`
- `../31_learning/_index.md`
