---
id: meaning_model.relationships.v1
status: planned
owner: 01_meaning_model
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 20_relationships.md — entity 間関係の語彙

## 役割

entity 同士をつなぐ関係（relationship）の語彙と方向を後段で体系化する。`10_entities.md` の自然文で書かれた関係を、再利用できる関係語彙として整理し、prompt / contract が関係を ID 参照できるようにする。

現状は `10_entities.md` の §主要な関係 が暫定正本。本 file はその抽象化先。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。関係を機械的に辿る必要（依存解析・投影先解決など）が生じた段階で active 化する。

## 持つもの（後段で本格実装する内容）

- 関係語彙の一覧：has / produces / evaluates / satisfies / depends_on / projects_to / attaches_to
- 各関係の方向（一方向か、許される向き）
- 各関係の定義域・値域（どの entity からどの entity へ）
- 関係の制約（双方向の禁止、書き戻し path の禁止など、後で追加する予定）

## 持たないもの

- entity 定義本体（→ `10_entities.md`）
- 分類軸（→ `30_taxonomies.md`）
- 推論ルール（→ `40_rules.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 関係が双方向化される（業務正本への書き戻しが語彙として許可される）

## 関連ファイル

- `10_entities.md`
- `30_taxonomies.md`
- `40_rules.md`
