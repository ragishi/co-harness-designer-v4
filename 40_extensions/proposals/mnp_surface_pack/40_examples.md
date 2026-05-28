---
id: mnp_pack.examples.v1
status: proposal
owner: mnp_surface_pack
---

# 40_examples.md — MNP 使用例

## 役割

MNP block の **使い方の具体例** を示す。

## 持つもの

- Topology / Workflow Lens / Member Work Lens の例
- 各例の正本 source_pin
- 業務正本の保護例

## 持たないもの

- 実 target repo の業務正本
- parser / serializer 実装

---

## 例 1: Topology Studio のノード・エッジ

````markdown
```mnp-surface
surface topology id="companyos_map"

node companyos "CompanyOS" type=hub
node note_repo "Note Production" type=repo
node youtube_repo "YouTube Ops" type=repo

companyos -> note_repo label="reads surface"
companyos -> youtube_repo label="reads surface"
```
````

正本: `note_repo` と `youtube_repo` の SPOKE.yml / README から source_pin で参照。

---

## 例 2: Workflow Lens

````markdown
```mnp-surface
surface workflow_lens id="note_production"

lane planned "予定"
lane active "進行中"
lane review_needed "レビュー待ち"
lane publish_ready "公開準備"
lane published "公開済み"

card article_001 "CompanyOS 設計記事"
  lane active
  status active
  source "../../20_workspace/articles/companyos-design/meta.md"
  owner "saku"
  next_action "本文レビュー"

card article_002 "Harness Designer V4 解説"
  lane review_needed
  status review_needed
  source "../../20_workspace/articles/hdv4-guide/meta.md"
  owner "saku"
  next_action "タイトル調整"
```
````

正本: 各記事の `meta.md`。**本文は MNP に含めない**。

---

## 例 3: Member Work Lens

````markdown
```mnp-surface
surface member_work_lens id="saku_today"

member saku "saku"

task task_001 "note 記事レビュー"
  status review_needed
  source "../../20_workspace/articles/hdv4/meta.md"
  repo "co-note-production"
  next_action "タイトル / 導入の確認"
  due "2026-05-30"

task task_002 "client repo 設計"
  status active
  source "../../20_workspace/client_repo_design/00_request.md"
  repo "co-harness-designer-v4"
  next_action "scope を固める"
  due "2026-05-29"
```
````

正本: 各 task の `meta.md`。**作業詳細は MNP に含めない**。

---

## 例 4: Repo Card

````markdown
```mnp-surface
surface repo_card id="co-note-production"

card repo "co-note-production"
  archetype "archetype.note_production_repo.v1"
  version "stable-baseline-v4-mvp"
  active_workflows 2
  active_tasks 5
  source "../../SPOKE.yml"
```
````

正本: target repo の `SPOKE.yml` / `README.md`。

---

## 禁止例（やってはいけない）

### 業務正本を MNP に書く（× MNP Not SSOT 違反）

````markdown
```mnp-surface
surface workflow_lens id="bad_example"

card article "今月の note"
  body "ここに記事本文を全部書いてしまう..."   ← ✗ 業務正本
```
````

### source なしで card / task を書く（× MNP Source Pin 違反）

````markdown
```mnp-surface
surface workflow_lens id="bad_example"

card task_x "なにかのタスク"
  status active
   ← source 属性が欠落 ✗
```
````

### enum 外の status（× MNP Contract 違反）

````markdown
```mnp-surface
surface workflow_lens id="bad_example"

card task_x "task"
  status doing   ← ✗ enum は active であるべき
  source "..."
```
````

### `.companyos/surfaces/` 外で MNP block（× MNP Location 違反）

```text
20_workspace/articles/foo/meta.md  ← ✗ ここに MNP block を置かない
```

---

## 関連ファイル

- `10_notation_rules.md`
- `20_parser_serializer_contract.md`
- `30_prompt_rules.md`
- `../../../02_contracts/80_mnp_surface_contract.md`
- `../../../06_build/scaffolds/companyos_interface/surfaces/`

## 最低 acceptance

- 例 1-4 が正常例として記載されている
- 禁止例 4 種類が明示されている
- すべての例で「正本は MNP ではない」が示されている

## 止める条件

- 業務正本を含む例が「正常例」として書かれた
- 禁止例が削除された
- source なしの例が「正常例」になった
