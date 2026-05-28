---
id: surface.member_work_lens.scaffold.v1
status: scaffold
source_pins:
  - path: "../../20_workspace/active/*/meta.md"
    field: "owner, status, next_action"
note: "雛形。target repo にコピーして実 source_pin で編集する。"
---

# member_work_lens.surface.md（雛形）

## 0. 目的

メンバー（=owner）視点で「今日やる仕事」を CompanyOS **Member Work Lens** に表示する Surface 定義の **雛形**。

## 1. 正本

| 情報 | 正本パス |
| --- | --- |
| owner 別の active task | `../../20_workspace/active/*/meta.md`（owner で grep） |
| task の next_action | 同上 |
| 期限 | 同上 |

## 2. 表示要素

- owner 別の active task list
- 各 task の status / next_action / due
- 関連 repo 名（archetype と組み合わせて表示）

## 3. UI 上の挙動

- Lens : Member Work Lens
- allowed_actions：task を開く、status を変える（変更は writeback intent として記録）

## 4. MNP block（任意）

````markdown
```mnp-surface
surface member_work_lens id="{member_id}_today"

member {member_id} "{member_name}"

task task_001 "{task_title}"
  status review_needed
  source "../../20_workspace/active/{slug}/meta.md"
  repo "{this_target_repo_name}"
  next_action "{next_action}"
  due "{YYYY-MM-DD}"
```
````

## 5. 注意

このSurfaceは UI 表示用であり、業務正本ではない。

UI から status / next_action を変更した場合は、`writeback intent` として `sync/` に記録し、人間承認後に source_pin 側の Markdown を更新する（業務正本への直接書き込みは禁止）。

## 関連 contract

scaffold 内では深い相対パスを避け、ID 参照 + V4 source pointer を使う。target repo へコピーされた後でも誤解しないため。

| contract / metric | V4 source |
| --- | --- |
| `contract.surface.v1` | `co-harness-designer-v4/02_contracts/40_surface_contract.md` |
| `contract.writeback.v1`（planned） | `co-harness-designer-v4/02_contracts/60_writeback_contract.md` |
| `semantic.workflow_status.v1` | `co-harness-designer-v4/03_status_metrics/10_workflow_status.md` |
| `contract.mnp_surface.v1`（MNP block を使う場合） | `co-harness-designer-v4/02_contracts/80_mnp_surface_contract.md` |
