---
id: learning.patterns.v1
status: planned
owner: 31_learning
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# patterns/ — 抽象化されたパターン置き場

## 役割

`signals/` から **冷却期間 ≥ 7 日** かつ **抽象化可能** と判断されたものを「パターン」として昇格させ、個別ファイルで管理する場所。
個別事象を超えて、より汎用的な言語で表現したパターンを記録する。
Stage 2 を通過したものだけがここに置かれる。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## このフォルダが持つもの

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口（本 file） | ✓ |
| `{pattern_id}.md` | 個別 pattern（Stage 2 通過後） | — 後段 |

**現状 entry なし — 昇格 protocol を通ったもののみ置く**

## このフォルダが持たないもの

- 未抽象化の兆候（→ `../signals/`、Stage 1）
- 採用候補（→ `../candidates/`、Stage 3 以降）
- raw 観測本体（→ `../../30_feedback/raw/{YYYY-MM}.md`）

## MVP での扱い

本 folder は MVP ではまだ使わない（active 化しない）。Stage 2 gate（冷却 ≥ 7 日 + 抽象化可能）を通過した pattern が初めて生まれたタイミングで実装する。

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- Stage 2 gate を通っていない entry がここに置かれる
- signal とパターンの区別が曖昧になる

## 関連ファイル

- `../00_promotion_protocol.md`（Stage 2 gate の詳細）
- `../signals/README.md` — 昇格元（Stage 1）
- `../candidates/README.md` — 昇格先（Stage 3）
