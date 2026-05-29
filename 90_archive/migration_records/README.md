---
id: archive.migration_records.v1
status: planned
owner: 90_archive
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# migration_records/ — rejected candidate・移行の理由付き記録

## 役割

`31_learning/00_promotion_protocol.md` の rejected ルートを経由して archive された候補や、
V3 → V4 などの migration の理由・経緯を**理由付きで記録**する場所。
「なぜ採用しなかったか」「なぜ変更したか」の意思決定の痕跡を残す。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本フォルダは MVP では空。
最初の rejected candidate または migration 完了（理由の記録が必要な変更）が発生したタイミングで実物を追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- rejected 候補の記録（何を・いつ・なぜ却下したか）
- migration 記録（V3 → V4 などの変更経緯・決定理由）
- 将来の参考のための「学び」への pointer（`../../31_learning/` へ）

## このフォルダが持たないもの

- 現役の learning（→ `../../31_learning/`）
- 完成した migration plan 正本（→ `../../21_outputs/migration_plans/`）
- archetype / contract の退役実体（→ `../retired_archetypes/` 等）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 理由なしの rejected 記録が置かれた
- migration records と retirement records が混在した

## 関連ファイル

- `../00_archive_policy.md` — 退役方針
- `../../31_learning/00_promotion_protocol.md` — rejected 経路
- `../../21_outputs/migration_plans/` — migration plan 完成版
- `../README.md` — 90_archive 全体
