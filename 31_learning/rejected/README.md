---
id: learning.rejected.v1
status: planned
owner: 31_learning
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# rejected/ — 却下済み置き場

## 役割

`candidates/` から **saku 6 択判断で却下** となったものを理由付きで保管する場所。
削除ではなく保管する — なぜ却下されたかを残すことで、同じ検討を繰り返さないようにする。
却下理由は将来の設計判断の参考資料となる。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## このフォルダが持つもの

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口（本 file） | ✓ |
| `{rejected_id}.md` | 個別却下済み entry（理由付き） | — 後段 |

**現状 entry なし — 昇格 protocol を通ったもののみ置く**

## このフォルダが持たないもの

- 採用済み entry（→ `../accepted/`）
- まだ判断が出ていない候補（→ `../candidates/`）
- 削除して消した内容（deleted は rejected で保管する）
- raw 観測（→ `../../30_feedback/raw/`）

## MVP での扱い

本 folder は MVP ではまだ使わない（active 化しない）。最初の却下判断が出たタイミングで実装する。

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 却下理由なしで entry が置かれる
- rejected の entry が削除される（削除禁止）

## 関連ファイル

- `../00_promotion_protocol.md`（Stage 4 gate と 6 択の詳細）
- `../candidates/README.md` — 昇格元（Stage 3）
- `../../90_archive/migration_records/README.md` — 長期保管先
