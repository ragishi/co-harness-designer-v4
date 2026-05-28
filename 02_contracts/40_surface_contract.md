# 40_surface_contract.md — UI 連携 (Surface) 契約

## 役割

target repo の正本情報を CompanyOS UI / Topology Studio に**どう表示するか**を定義する。

これが「Repo → UI」の中核契約。

## 持つもの

- Surface とは何か（再掲）
- Surface ファイル（`.companyos/surfaces/*.surface.md`）の構造
- Surface が持ってよいもの / 持ってはいけないもの
- source_pin の必須化

## 持たないもの

- Surface の中身（archetype / target repo 側）
- exporter の実装（→ `../06_build/exporters/`）
- entity 定義（→ `../01_meaning_model/10_entities.md`）

## Surface とは何か

**Surface = Repo 正本を CompanyOS UI に表示するための「見せ方定義」**

- 正本ではない（業務正本は target repo の通常 directory）
- 業務正本から生成・参照される
- UI が壊れても、業務正本は無傷である（P0）

## Surface ファイルの構造

```markdown
---
id: surface.{repo}.{name}.{version}
status: active | draft | deprecated
source_pins:
  - path: "../../20_workspace/articles/{slug}/meta.md"
    field: "title"
  - path: "../../02_workflows/note_article_production.md"
---

# {surface_title}

## 0. 目的
このファイルは、{repo_name} の {what} を CompanyOS の {lens_name} に表示するための Surface 定義である。

## 1. 正本
このSurfaceの業務正本は以下にある。

| 情報 | 正本パス |
| --- | --- |
| ... | `../../20_workspace/.../meta.md` |

## 2. 表示要素
（MNP block または自然文表で）

## 3. UI 上の挙動
- どの Lens に出るか
- どのカード / ノード / レーンに出るか
- allowed_actions

## 4. 注意
このSurfaceは UI 表示用であり、業務正本ではない。
業務正本を変更する場合は source_pin 側の Markdown を編集する。
```

## Surface が持ってよいもの

- UI 上のカード / ノード / エッジ
- 表示グループ（lane / column）
- 並び順
- source_path への参照
- status の投影（`../03_status_metrics/10_workflow_status.md` の enum）
- allowed_actions の表示
- MNP block（中間記法、`80_mnp_surface_contract.md` 準拠）

## Surface が持ってはいけないもの

- 業務正本（記事本文、台本、納品物、WBS 本体、Prompt 正本、SSOT ルール、feedback / learning 原本）

## source_pin 必須

Surface 内で表示するすべての情報は、`source_pins` で業務正本への参照を持つ。
source_pin がない情報は Critical Gate `Source Pin Gate` で止める。

## 最低 acceptance

- frontmatter に id / status / source_pins がある
- 業務正本パスが少なくとも 1 つ参照されている
- 「UI 表示用であり業務正本ではない」明記

## 止める条件

- Surface 内に業務正本（記事本文など）がコピーされた
- source_pin がない情報が含まれている
- status が enum 外を使っている
- 直接書き戻し path が記述されている

## 関連ファイル

- `00_contract_map.md`
- `10_repo_contract.md`
- `70_markdown_contract.md`
- `80_mnp_surface_contract.md`
- `../03_status_metrics/10_workflow_status.md`
- `../06_build/scaffolds/companyos_interface/surfaces/`（雛形）
