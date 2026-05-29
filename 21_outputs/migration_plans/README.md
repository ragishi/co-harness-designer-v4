---
id: output.migration_plans.v1
status: planned
owner: 21_outputs
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# migration_plans/ — migration package の完成版

## 役割

`00_foundation/04_decision_rules.md` の 6-step migration package プロセスを経て完成した **migration 計画書の最終版** を置く場所。
V3 → V4、archetype 廃止、contract 変更など、L2 以上の変更には migration package が必要。
完成した migration plan はここに保管し、`90_archive/migration_records/` と連動する。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
最初の migration package 完成時（L2 以上の変更が発生したとき）に実物を追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- 完成した migration package（6-step フォーマット）
- 変更対象・変更理由・影響範囲・ロールバック手順
- 完成日・承認記録への pointer

## このフォルダが持たないもの

- 作業中の migration ドラフト（→ `../../20_workspace/`）
- 退役記録（→ `../../90_archive/migration_records/`）
- DRR 判断基準正本（→ `../../00_foundation/04_decision_rules.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 6-step フォーマット未完のものが「完成版」として置かれた
- ドラフトと完成版の区別が消えた

## 関連ファイル

- `../../00_foundation/04_decision_rules.md` — DRR + 6-step migration package
- `../../90_archive/migration_records/` — 退役・rejected 記録
- `../README.md` — 21_outputs 全体
