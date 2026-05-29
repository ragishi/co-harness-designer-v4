---
id: archetype.template.definition.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# archetype_definition.md — archetype 定義の空枠雛形

## 役割

新 archetype の定義本文（`../repo/{name}.md`）を書くときの**空枠雛形**。`../repo/note_production_repo.md` と同じ section 構成を空欄で並べ、埋めるだけで archetype 定義が完成するようにする。section 順序・必須項目を逸脱させないためのガイド。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。新 archetype を起こすときに、この雛形を `../repo/{name}.md` にコピーして各 section を埋める。

## 持つもの（後段で本格実装する内容）

- frontmatter 雛形（`id: archetype.{name}.v1` / `status: draft` / `owner: 04_archetypes`）
- 標準 section の空枠：目的 / 必須 module / 推奨 module / 禁止 module / 持つべき workflow / CompanyOS に表示するもの / 表示しないもの / archetype 固有 root / quality_profile / 関連 contract / 最低 acceptance / 止める条件
- 各 section の記入ヒント（何を書くか1行）

## 持たないもの

- 必須/推奨/禁止 module の宣言雛形（→ `required_modules.md`）
- archetype 固有 root の構造雛形（→ `recommended_structure.md`）
- quality_profile の雛形（→ `quality_profile.md`）
- 既存 archetype の本文（→ `../repo/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- 雛形の section 順が active archetype（`../repo/note_production_repo.md`）と一致すると読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- active archetype と section 順がずれた雛形を書く

## 関連ファイル

- `../repo/note_production_repo.md`
- `../00_archetype_framework.md`
- `required_modules.md`
- `recommended_structure.md`
- `quality_profile.md`
