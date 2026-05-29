---
id: learning.promotion_queue.v1
status: planned
owner: 31_learning
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# promotion_queue.md — 昇格待ちキュー

## 役割

各 stage で昇格判断を待っている entry を一覧化し、昇格の進捗を可視化する場所。
どの entry が Stage 1 / 2 / 3 / 4 のどこで止まっているか、次のアクションが何かを管理する。
昇格 protocol（`00_promotion_protocol.md`）の **実行状態の追跡** がここの役割であり、protocol 本体はここには書かない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。最初の昇格候補が生まれた（signals に entry が置かれた）タイミングで実装する。

## 持つもの（後段で本格実装する内容）

- 各 stage 別の昇格待ち entry 一覧（id / 現 stage / 次アクション / 担当）
- 各 stage の gate 通過状況チェックリスト
- 直近の昇格・却下イベントのログ（最新 N 件）

## 持たないもの

- 昇格 protocol 本体（→ `00_promotion_protocol.md`）
- entry の本文（→ 各 `signals/` `patterns/` `candidates/` `accepted/` `rejected/`）
- raw 観測（→ `../../30_feedback/raw/`）

## 現状

昇格待ちキュー: **空**（entry なし）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 昇格 protocol の gate 条件がここで変更される
- キューの状態と entry 本体が混同される

## 関連ファイル

- `00_promotion_protocol.md`
- `_index.md`
- `signals/README.md`
- `patterns/README.md`
- `candidates/README.md`
