---
id: archetype.template.required_modules.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# required_modules.md — 必須 / 推奨 / 禁止 module 宣言の雛形

## 役割

新 archetype が depends_on する Optional Module を「必須 / 推奨 / 禁止」に分けて宣言するための**雛形**。`../20_optional_modules.md` の 8 module から選び、理由を添えて宣言する形を提供する。archetype → module は一方向（module は archetype を知らない）。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。新 archetype 作成時に、この雛形に沿って module 構成を確定し `../repo/{name}.md` の該当 section へ転記する。

## 持つもの（後段で本格実装する内容）

- 必須 module 宣言の雛形（`content_production` / `publish_pipeline` / `client_ops` / `project_management` など `../20_optional_modules.md` の id を参照）
- 推奨 module 宣言の雛形（`analytics_ops` / `automation_pack` など）
- 禁止 module 宣言の雛形（理由を必ず併記）
- `feedback_loop`（built-in、Common Core）の扱い説明

## 持たないもの

- module の実体・実装（→ `../../40_extensions/installed/{module}/`、MVP では空）
- archetype 定義の他 section（→ `archetype_definition.md`）
- 固有 root 構造（→ `recommended_structure.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- 必須 / 推奨 / 禁止の 3 区分と「禁止には理由を併記」が読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- `../20_optional_modules.md` に無い module を雛形に書く
- module が archetype を depends_on する逆方向の記述

## 関連ファイル

- `../10_common_core.md`
- `../20_optional_modules.md`
- `archetype_definition.md`
- `../../40_extensions/00_extension_policy.md`
