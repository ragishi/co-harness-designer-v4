---
id: workspace.{slug}.02_archetype_choice.v1
status: draft
slug: "{YYYY-MM-{slug}}"
---

# 02_archetype_choice.md — 使う archetype

## 役割

この設計作業で使う / 産む archetype を選ぶ。

## 持つもの

- 選んだ archetype（ID）
- 選択理由
- 必須 module / 推奨 module の選択

## 持たないもの

- archetype 定義本体（→ `../../../04_archetypes/repo/{archetype}.md` を ID 参照）

## 選んだ archetype

| ID | 理由 |
| --- | --- |
| `archetype.{name}.v1` |  |

## 必須 module（archetype 定義に従う）

- 

## 推奨 module（任意で採用）

- 

## 禁止 module（archetype 定義により）

- 

## 関連 file

- `../../../04_archetypes/repo/{archetype}.md`
- `../../../04_archetypes/00_archetype_framework.md`

## 最低 acceptance

- 選んだ archetype の ID が明示
- 選択理由が 1-3 行
- 必須 module / 禁止 module が archetype 定義と一致

## 止める条件

- 禁止 module を install しようとしている
- archetype 定義にない module を「必須」に追加した
- 選択理由が「便利そう」のような曖昧記述

## 次の step

`03_ssot_map.md` で正本の置き場所を決める。
