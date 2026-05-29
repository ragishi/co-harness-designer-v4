---
id: learning.index.v1
status: planned
owner: 31_learning
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# _index.md — 昇格パス navigate 入口

## 役割

`31_learning/` 全体を横断する **navigate 索引**。
signals → patterns → candidates → accepted / rejected の各層と、
昇格待ちキュー（`promotion_queue.md`）へのポインタを一覧化する。
読者が「どの stage に何があるか」「どの entry が昇格待ちか」を素早く把握できるように設計する。
raw 観測は扱わず、`30_feedback/` との境界を明確に保つ。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。各層に entry が蓄積され navigate の必要性が生まれたタイミングで実装する。

## 持つもの（後段で本格実装する内容）

- 昇格パス全体の鳥瞰図（5 段階 + rejected の方向を含む）
- signals / patterns / candidates / accepted / rejected 各層の entry 一覧へのポインタ
- `promotion_queue.md` へのポインタ（現在の昇格待ち状況）
- 最終更新日

## 持たないもの

- raw 観測本体（→ `../30_feedback/raw/`）
- 判断本体（→ `promotion_queue.md` と saku 6 択）
- 昇格 protocol 本体（→ `00_promotion_protocol.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- raw 観測がこのファイルに混入する
- 昇格 protocol を bypass する記述が含まれる

## 関連ファイル

- `00_promotion_protocol.md`
- `signals/README.md`
- `patterns/README.md`
- `candidates/README.md`
- `accepted/README.md`
- `rejected/README.md`
- `promotion_queue.md`
- `../30_feedback/_index.md`
