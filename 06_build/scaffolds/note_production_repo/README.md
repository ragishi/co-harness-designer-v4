---
id: build.scaffold.note_production_repo.v1
status: planned
owner: 06_build
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# scaffolds/note_production_repo/ — note_production archetype 雛形

## 役割

`note_production_repo` archetype を持つ target repo にコピーするための **雛形フォルダ**。
note 記事制作フローに特化した構造（記事ステータス・制作ログ・公開管理など）を雛形として提供する。

MVP では本フォルダは空のプレースホルダーとして住所を確保する。後段で `04_archetypes/repo/note_production_repo.md` の仕様が固まった時点で雛形構造を本格実装する。

**planned stub であり、後段で本格実装する（仕様であり実装コードではない）。住所と役割の確保。**

## このフォルダが持つもの

後段で本格実装した際に持つ内容：

| path | 役割 |
| --- | --- |
| `README.md` | このフォルダの入口（本ファイル） |
| `.companyos/` → | `../companyos_interface/` を参照（コピー元） |
| `articles/` | 記事メタデータ・ステータス雛形 |
| `production_log/` | 制作ログ雛形 |
| `publish/` | 公開管理雛形 |

## このフォルダが持たないもの

- 業務正本（実記事本文や制作データ）
- archetype 仕様の本文（→ `../../../04_archetypes/repo/note_production_repo.md`）
- 実装コード本体

## MVP での扱い

本フォルダは MVP ではまだ使わない（active 化しない）。`04_archetypes/repo/note_production_repo.md` の仕様が active になった後に本格実装する。co-note-production へのこの雛形適用は Phase 3 Explicit Consent Gate を経てから行う。

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- exporter が業務正本を直接書き換える設計
- 雛形に実記事本文や業務正本が混入した
- Phase 3 Explicit Consent Gate なしに co-note-production へ適用しようとする

## 関連ファイル

- `../../../04_archetypes/repo/note_production_repo.md` — archetype 仕様
- `../companyos_interface/README.md` — `.companyos/` コピー元
- `../base_repo/README.md` — 共通最小雛形（後段）
