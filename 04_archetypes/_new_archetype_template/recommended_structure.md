---
id: archetype.template.recommended_structure.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# recommended_structure.md — archetype 固有 root 構造の雛形

## 役割

新 archetype が産む target repo のディレクトリ構造を書くための**雛形**。Common Core 9 entries（`../../02_contracts/10_repo_contract.md`）を base に、archetype 固有 root（`02_workflows/` や `10_assets/` など）を追記する形を提供する。Common Core を欠かさず、固有 root を明示的に分けて書かせる。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。新 archetype 作成時に、この雛形の ASCII ツリーを埋めて固有 root を確定し `../repo/{name}.md` へ転記する。

## 持つもの（後段で本格実装する内容）

- Common Core 9 entries の固定ブロック（README.md / SPOKE.yml + 7 root directories + `.companyos/`）
- archetype 固有 root を追記する空欄ブロック（ASCII ツリー雛形）
- 固有 root と Common Core を視覚的に分ける書き方ガイド

## 持たないもの

- Common Core 契約本体（→ `../../02_contracts/10_repo_contract.md`）
- module ごとの追加 folder 例（→ `../20_optional_modules.md`）
- 必須/推奨/禁止 module 宣言（→ `required_modules.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- Common Core 9 entries を base に固有 root を追記する構造だと読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- Common Core 9 entries のいずれかを欠いた雛形を書く
- 固有 root を Common Core として混入させる

## 関連ファイル

- `../../02_contracts/10_repo_contract.md`
- `../10_common_core.md`
- `../20_optional_modules.md`
- `required_modules.md`
