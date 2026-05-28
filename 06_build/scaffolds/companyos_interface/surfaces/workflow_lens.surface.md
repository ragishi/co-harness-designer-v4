---
id: surface.workflow_lens.scaffold.v1
status: scaffold
source_pins:
  - path: "../../02_workflows/"
    field: "workflow definitions"
  - path: "../../20_workspace/active/*/meta.md"
    field: "current status per slug"
note: "雛形。target repo にコピーして実 source_pin で編集する。"
---

# workflow_lens.surface.md（雛形）

## 0. 目的

target repo の workflow 進行を CompanyOS **Workflow Lens** に表示する Surface 定義の **雛形**。

## 1. 正本

| 情報 | 正本パス |
| --- | --- |
| workflow 定義 | `../../02_workflows/*.md` |
| 各 instance の進行状態 | `../../20_workspace/active/*/meta.md` |
| phase enum | `../../../03_status_metrics/10_workflow_status.md`（V4 側） |

## 2. 表示要素

- workflow ごとの phase 進行（lane / column）
- 各 phase の active task カード
- task ごとの status badge

## 3. UI 上の挙動

- Lens : Workflow Lens
- allowed_actions：task カードを開く、workflow 定義を開く

## 4. MNP block（任意）

````markdown
```mnp-surface
surface workflow_lens id="{workflow_id}"

lane planned "予定"
lane active "進行中"
lane review_needed "レビュー待ち"
lane publish_ready "公開準備"
lane published "公開済み"

card task_001 "{task_title}"
  lane active
  status active
  source "../../20_workspace/active/{slug}/meta.md"
  owner "{owner}"
  next_action "{next_action}"
```
````

## 5. 注意

このSurfaceは UI 表示用であり、業務正本ではない。
業務正本（task 本体、進行状態）を変更する場合は source_pin 側の Markdown を編集する。

## 関連 contract

- `../../../../../02_contracts/40_surface_contract.md`
- `../../../../../02_contracts/20_workflow_contract.md`
- `../../../../../03_status_metrics/10_workflow_status.md`
