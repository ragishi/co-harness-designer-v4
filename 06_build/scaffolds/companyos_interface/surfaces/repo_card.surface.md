---
id: surface.repo_card.scaffold.v1
status: scaffold
source_pins:
  - path: "../../README.md"
    field: "title"
  - path: "../../SPOKE.yml"
    field: "spoke_id, archetype, version"
note: "雛形。target repo にコピーして source_pin を実 path で埋める。"
---

# repo_card.surface.md（雛形）

## 0. 目的

このファイルは、target repo を CompanyOS の **Repo Card** として表示するための Surface 定義の **雛形**。

target repo にコピーして source_pin を実 path で埋める。

## 1. 正本

このSurfaceの業務正本は以下にある。

| 情報 | 正本パス |
| --- | --- |
| repo タイトル | `../../README.md` |
| spoke_id / archetype / version | `../../SPOKE.yml` |
| 進行中 workflow | `../../02_workflows/` and `../../20_workspace/active/*/meta.md` |
| 進行中 task の件数 | `../../20_workspace/active/*/meta.md` |

## 2. 表示要素

CompanyOS Repo Card には以下を表示する：

- repo 名（README タイトル）
- archetype アイコン
- version
- 進行中 workflow 数
- 進行中 task 数
- 最後の更新日時（freshness）

## 3. UI 上の挙動

- どの Lens に出るか：Repo Card Lens、Topology Studio のノード
- allowed_actions：repo 詳細を開く、関連 task を見る

## 4. MNP block（任意、optional extension が install されている場合のみ）

````markdown
```mnp-surface
surface repo_card id="{target_repo_name}"

card repo "{repo_name}"
  archetype {archetype_id}
  version {version}
  active_workflows {count}
  active_tasks {count}
  source "../../SPOKE.yml"
```
````

## 5. 注意

このSurfaceは UI 表示用であり、業務正本ではない。
業務正本を変更する場合は source_pin 側の Markdown を編集する。

## 関連 contract

scaffold 内では深い相対パスを避け、ID 参照 + V4 source pointer を使う。target repo へコピーされた後でも誤解しないため。

| contract / metric | V4 source |
| --- | --- |
| `contract.surface.v1` | `co-harness-designer-v4/02_contracts/40_surface_contract.md` |
| `contract.mnp_surface.v1` | `co-harness-designer-v4/02_contracts/80_mnp_surface_contract.md` |
| `contract.markdown.v1` | `co-harness-designer-v4/02_contracts/70_markdown_contract.md` |
