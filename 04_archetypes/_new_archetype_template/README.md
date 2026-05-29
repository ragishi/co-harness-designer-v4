---
id: archetype.new_template.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# _new_archetype_template/ — 新 archetype 作成テンプレ入口

## 役割

新しい archetype を追加するときの**作成テンプレ一式**の入口。新 archetype は必ず本 template をコピーして埋め、DRR 5 質問を通してから `repo/{new_name}.md` として正式化する。テンプレを通さない archetype 追加は禁止（`../00_archetype_framework.md` の追加プロセス参照）。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 folder は MVP ではまだ使わない（active 化しない）。9 番目の archetype を追加する必要が生じたときに、本 template を起点として作成プロセスを回す。

## このフォルダが持つもの（後段で本格実装する内容）

| file | 役割 | status |
| --- | --- | --- |
| `README.md` | テンプレ入口（本 file） | 後段 |
| `archetype_definition.md` | archetype 定義の空枠雛形 | 後段 |
| `required_modules.md` | 必須/推奨/禁止 module 宣言の雛形 | 後段 |
| `recommended_structure.md` | archetype 固有 root 構造の雛形 | 後段 |
| `quality_profile.md` | archetype 別 quality_profile の雛形 | 後段 |

## このフォルダが持たないもの

- 個別 archetype の本文（→ `../repo/{name}.md`）
- Common Core の定義（→ `../10_common_core.md`）
- DRR の本体（→ `../../00_foundation/04_decision_rules.md`）
- DRR Gate の判定基準（→ `../../07_quality/30_critical_gates.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- 新 archetype が「template + DRR 5 質問」を通す必要があると読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- template を通さずに `../repo/` へ archetype を追加する運用を許す記述

## 関連ファイル

- `../00_archetype_framework.md`
- `../../00_foundation/04_decision_rules.md`
- `../../07_quality/30_critical_gates.md`
- `../repo/README.md`
