---
id: status_metric.task_status.v1
status: planned
owner: 03_status_metrics
note: "住所と役割確保のための stub。本格実装は後段。MVP では workflow_status の 8 enum を流用する。"
---

# 20_task_status.md — task の共通 status

## 役割

V4 が産む全 target repo の **Task** で使う status enum を定義する。

**planned stub であり後段で本格実装する。** MVP では `10_workflow_status.md` の 8 enum を Task status としても流用するため、本 file を active 化しない。

## MVP での扱い

**MVP では `10_workflow_status.md` の 8 enum（`planned / active / review_needed / blocked / publish_ready / published / learning / archived`）を task status としても使う。**

Task 固有の status enum が必要になるかどうかは運用データが蓄積してから判断する。

### 新 enum を勝手に追加しない（重要）

- task 固有 enum を追加する前に、`10_workflow_status.md` の 8 enum で代替できるか必ず確認する
- 追加が正当化される条件: 同じ問題が 3 回以上再発し、かつ DRR（Drift Rejection Rule）5 question を通過した場合のみ
- 承認なしに enum を追加した場合、それは `10_workflow_status.md` の止める条件「status enum が 8 を超えて増えた」に抵触する

### `01_meaning_model/10_entities.md` §4 Task との整合

`10_entities.md` §4 Task の `status` 属性は `../03_status_metrics/10_workflow_status.md` の enum を参照している。本 file が active 化されたら、そのポインターをここへ移行する。

## 持つもの

- Task 固有 status enum（後段で定義）
- Task status 遷移ルール（後段で定義）
- workflow_status との継承関係・差分説明

## 持たないもの

- workflow の status enum（→ `10_workflow_status.md`）
- artifact の status（→ `30_artifact_status.md`）
- CompanyOS 変換マッピング（→ `mapping_rules/local_status_to_companyos.md`）
- 計算実装

## 最低 acceptance

- 本 stub の存在意義が読める
- MVP では workflow_status の 8 enum を流用することが明記されている
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- DRR 未通過で task 固有 enum を追加する
- `10_workflow_status.md` の 8 enum と矛盾する enum を定義する

## 関連ファイル

- `10_workflow_status.md`（MVP での流用元 enum 定義）
- `../01_meaning_model/10_entities.md` §4（Task entity の status pointer）
- `mapping_rules/local_status_to_companyos.md`（CompanyOS 変換）
