---
id: workspace.{slug}.06_surface_design.v1
status: draft
slug: "{YYYY-MM-{slug}}"
---

# 06_surface_design.md — UI への見せ方

## 役割

target repo が CompanyOS UI / Topology Studio に **どう見えるか** を具体に設計する。

## 持つもの

- 各 surface の表示要素
- source_pin の具体
- MNP block を使うか（任意）

## 持たないもの

- 業務正本本体
- surface_contract 本文（→ `../../../02_contracts/40_surface_contract.md`）

## 各 surface

### repo_card.surface.md

- 表示要素: repo 名 / archetype / version / active task 数
- source_pin: `README.md`, `SPOKE.yml`

### workflow_lens.surface.md

- 表示要素: workflow ごとの phase 進行
- source_pin: `02_workflows/`, `20_workspace/active/*/meta.md`

### member_work_lens.surface.md

- 表示要素: owner ごとの active task
- source_pin: `20_workspace/active/*/meta.md`

### archetype 固有の surface

- 

## MNP block の使用

- [ ] 使う
- [ ] 使わない（MVP 推奨）

MNP block を使う場合は `../../../02_contracts/80_mnp_surface_contract.md` の制約を遵守する。

## 関連 file

- `../../../06_build/scaffolds/companyos_interface/surfaces/`
- `../../../02_contracts/40_surface_contract.md`

## 最低 acceptance

- 3 surface に表示要素と source_pin が記載されている
- 業務正本本体が surface に含まれていない
- 「UI 表示用であり業務正本ではない」明記

## 止める条件

- 業務正本が surface に含まれた
- source_pin がない表示要素がある
- writeback path が直接 surface に記述された

## 次の step

`07_quality_plan.md` で品質ゲートを確定する。
