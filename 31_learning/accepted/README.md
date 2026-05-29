---
id: learning.accepted.v1
status: planned
owner: 31_learning
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# accepted/ — 採用済み置き場

## 役割

`candidates/` から **boundary check pass** かつ **saku 6 択判断で採用** となったものを保管し、
`00_foundation/` 〜 `07_quality/` の正式設計への反映状態を追跡する場所。
Stage 4 の全 gate を通過したものだけがここに置かれる。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## このフォルダが持つもの

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口（本 file） | ✓ |
| `{accepted_id}.md` | 個別採用済み entry（Stage 4 通過後） | — 後段 |

**現状 entry なし — 昇格 protocol を通ったもののみ置く**

## このフォルダが持たないもの

- boundary check 未通過の candidate（→ `../candidates/`）
- 却下済み entry（→ `../rejected/`）
- 正式設計本体（→ `../../00_foundation/` 〜 `../../07_quality/`）
- raw 観測（→ `../../30_feedback/raw/`）

## MVP での扱い

本 folder は MVP ではまだ使わない（active 化しない）。Stage 4 gate（boundary check pass + saku 6 択採用）を通過した entry が初めて生まれたタイミングで実装する。

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 昇格 protocol を bypass して直接書き込まれる（saku 6 択なしの採用は禁止）
- 採用済み entry が正式設計に反映されないまま放置される

## 関連ファイル

- `../00_promotion_protocol.md`（Stage 4 gate の詳細）
- `../candidates/README.md` — 昇格元（Stage 3）
- `../../00_foundation/` 〜 `../../07_quality/` — 反映先
