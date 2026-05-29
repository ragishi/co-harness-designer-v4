---
id: learning.signals.v1
status: planned
owner: 31_learning
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# signals/ — 兆候置き場

## 役割

`30_feedback/raw/` で **同一事象が再発 ≥ 3 回** 観測されたものを「兆候」として昇格させ、個別ファイルで追跡する場所。
まだパターンではなく、繰り返しが確認された事実の記録にとどまる。
Stage 1 を通過したものだけがここに置かれる。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## このフォルダが持つもの

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口（本 file） | ✓ |
| `{signal_id}.md` | 個別 signal（Stage 1 通過後） | — 後段 |

**現状 entry なし — 昇格 protocol を通ったもののみ置く**

## このフォルダが持たないもの

- raw 観測本体（→ `../../30_feedback/raw/{YYYY-MM}.md`）
- 抽象化されたパターン（→ `../patterns/`、Stage 2 以降）
- 採用候補（→ `../candidates/`）
- 判断（→ `../accepted/` / `../rejected/`）

## MVP での扱い

本 folder は MVP ではまだ使わない（active 化しない）。Stage 1 gate（再発 ≥ 3、別 entry）を通過した signal が初めて生まれたタイミングで実装する。

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- Stage 1 gate を通っていない entry がここに置かれる
- raw 観測が直接ここに書かれる

## 関連ファイル

- `../00_promotion_protocol.md`（Stage 1 gate の詳細）
- `../../30_feedback/raw/` — raw 供給元
- `../patterns/README.md` — 昇格先（Stage 2）
