---
id: feedback.archetype.v1
status: planned
owner: 30_feedback
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# archetype_feedback.md — archetype フィードバック集約入口

## 役割

`30_feedback/raw/` に蓄積された観測の中で **archetype に関する FEV** を横断的に集約する入口。
`04_archetypes/` 配下の各 repo 原型（note / client / SNS / YouTube / project_mgmt / workflow_ops / prompt / design_system）に関する観測、
archetype の汎用性・適用精度・template 設計への違和感などを対象とする。
判断・抽象化は行わず、raw からの集約 pointer を管理するだけ。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。archetype 関連の FEV が raw に複数件蓄積され、集約の必要性が生まれたタイミングで実装する。

## 持つもの（後段で本格実装する内容）

- `raw/{YYYY-MM}.md` から archetype カテゴリ FEV への逆引きリンク
- 影響する archetype ファイルへのポインタ（`../04_archetypes/`）
- 繰り返し出現している観測の列挙（判断なし）

## 持たないもの

- 判断・抽象化（→ `../31_learning/`）
- raw 本体（append は `raw/{YYYY-MM}.md` に行う）
- archetype 本体の変更提案（→ 昇格プロセスを経ること）
- target repo への直接適用指示（Phase 3 は explicit consent gate を経ること）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- archetype 適用の判断がここに書かれる
- target repo 編集への言及が混入する

## 関連ファイル

- `raw/{YYYY-MM}.md`
- `_index.md`
- `../04_archetypes/README.md` — archetype root
- `../31_learning/00_promotion_protocol.md`
- `../../CLAUDE.gate.md` — Phase 3 consent gate
