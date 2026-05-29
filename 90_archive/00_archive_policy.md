---
id: archive.policy.v1
status: planned
owner: 90_archive
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 00_archive_policy.md — 退役方針

## 役割

`90_archive/` に何を・いつ・どのように保管するかの**退役方針**を定義する。
「削除しない、退役する」思想の明文化。退役理由・代替先・復元手順を必ず記録するルール。
`migration_records/` との連携、`31_learning/00_promotion_protocol.md` の rejected 経路との関係も記述する。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。
最初の退役対象（retired archetype / contract 等）が発生する前に本格実装する。

## このファイルが持つもの（後段で本格実装する内容）

- 退役対象の種別（archetype / contract / scaffold / output）ごとの退役手順
- 退役に必要な記録項目（退役理由・代替先・退役日・承認者）
- 「削除しない」原則と git history の使い分け
- `migration_records/` の役割（rejected candidate / migration 理由付き記録）
- `31_learning/00_promotion_protocol.md` の rejected ルートとの接続

## このファイルが持たないもの

- 現役の正本（→ 各正本の場所）
- learning の昇格・退役判断（→ `../31_learning/00_promotion_protocol.md`）
- DRR 判断基準（→ `../00_foundation/04_decision_rules.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 退役理由のない archive ルールが追加された
- 現役のものを archive する手順が書かれた（現役 vs 退役の混同）

## 関連ファイル

- `README.md` — 90_archive 全体
- `99_legacy_v3_pointer.md` — V3 への pointer
- `migration_records/README.md` — 移行・rejected 記録
- `../31_learning/00_promotion_protocol.md` — rejected 経路
