---
id: archetype.template.quality_profile.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# quality_profile.md — archetype 別 quality_profile の雛形

## 役割

新 archetype に固有の品質プロファイルを宣言するための**雛形**。共通 quality（`../../07_quality/10_common_quality.md`、全 archetype 適用）に加え、archetype 固有の critical gate を `../../07_quality/20_archetype_quality.md` の枠組みに沿って定義する形を提供する。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。新 archetype 作成時に、この雛形へ固有 gate を埋めて `../repo/{name}.md` の quality_profile section へ転記する。

## 持つもの（後段で本格実装する内容）

- 共通 quality を全適用する宣言ブロック（base）
- archetype 固有 critical gate の空欄リスト（例：制作物の必須 field / 公開準備 gate）
- advisory gate（任意適用）の雛形
- gate と `../../02_contracts/` の整合チェック項目

## 持たないもの

- 共通 quality の本体（→ `../../07_quality/10_common_quality.md`）
- archetype quality 枠組みの定義（→ `../../07_quality/20_archetype_quality.md`）
- DRR Gate / critical gate の判定基準（→ `../../07_quality/30_critical_gates.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- 「共通 quality 全適用 + archetype 固有 gate」の二層構造が読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 共通 quality の本体を本 file に複製する
- gate の判定基準を `../../07_quality/` から切り離して再定義する

## 関連ファイル

- `../../07_quality/20_archetype_quality.md`
- `../../07_quality/10_common_quality.md`
- `../../07_quality/30_critical_gates.md`
- `archetype_definition.md`
