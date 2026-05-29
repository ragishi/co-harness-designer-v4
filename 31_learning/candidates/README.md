---
id: learning.candidates.v1
status: planned
owner: 31_learning
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# candidates/ — 採用候補置き場

## 役割

`patterns/` から **grader pass** かつ **関連 contract / archetype 識別** が完了したものを「採用候補」として昇格させ、管理する場所。
grader（AI または human）が妥当と判断し、どこに反映するかが明確になったパターンを記録する。
Stage 3 を通過したものだけがここに置かれ、最終的に saku 6 択判断を待つ。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## このフォルダが持つもの

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口（本 file） | ✓ |
| `{candidate_id}.md` | 個別 candidate（Stage 3 通過後） | — 後段 |

**現状 entry なし — 昇格 protocol を通ったもののみ置く**

## このフォルダが持たないもの

- grader 未通過のパターン（→ `../patterns/`）
- 採用済み entry（→ `../accepted/`）
- 却下済み entry（→ `../rejected/`）
- raw 観測本体（→ `../../30_feedback/raw/{YYYY-MM}.md`）

## MVP での扱い

本 folder は MVP ではまだ使わない（active 化しない）。Stage 3 gate（grader pass + 反映先識別）を通過した candidate が初めて生まれたタイミングで実装する。

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- grader pass 前の entry がここに置かれる
- saku 6 択判断を経ずに accepted / rejected に移動される

## 関連ファイル

- `../00_promotion_protocol.md`（Stage 3 gate の詳細）
- `../patterns/README.md` — 昇格元（Stage 2）
- `../accepted/README.md` — 昇格先（Stage 4 採用）
- `../rejected/README.md` — 昇格先（Stage 4 却下）
- `promotion_queue.md` — 昇格待ちキュー
