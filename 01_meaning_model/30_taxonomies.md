---
id: meaning_model.taxonomies.v1
status: planned
owner: 01_meaning_model
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 30_taxonomies.md — entity の分類軸

## 役割

entity を横断的に分類する軸（taxonomy）を後段で定義する。entity 定義そのものではなく、entity に付ける「タグ的な分類の語彙」を集約し、prompt / contract / read_set が同じ分類語で entity を絞り込めるようにする。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。分類軸で entity やコンテンツを機械的に振り分ける必要が生じた段階で active 化する。

## 持つもの（後段で本格実装する内容）

- `task_type` — Task の種別分類軸
- `risk_level` — リスク水準の分類軸
- `archetype tag` — archetype を指す分類タグ（本体ではなく参照タグ）
- `content_type` — コンテンツ種別の分類軸
- 各軸の値域と相互排他性の方針（後で追加する予定）

## 持たないもの

- entity 定義本体（→ `10_entities.md`）
- status enum（→ `../03_status_metrics/`）
- archetype 本体（→ `../04_archetypes/`、ここはタグ参照のみ）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- status enum や archetype 本体をここに定義し始める（所有権の侵害）

## 関連ファイル

- `10_entities.md`
- `20_relationships.md`
- `40_rules.md`
- `../03_status_metrics/00_status_map.md`
- `../04_archetypes/00_archetype_framework.md`
