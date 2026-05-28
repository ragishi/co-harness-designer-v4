---
id: workspace.{slug}.05_contract_design.v1
status: draft
slug: "{YYYY-MM-{slug}}"
---

# 05_contract_design.md — 連携契約

## 役割

target repo が遵守する contract と、target が出す `.companyos/manifest.md` の内容を確定する。

## 持つもの

- 遵守する contract 一覧
- manifest 概要
- expose する surface 一覧

## 持たないもの

- contract 本文（→ `../../../02_contracts/`）
- surface 本文（→ `06_surface_design.md`）

## 遵守する contract

| contract ID | 役割 |
| --- | --- |
| `contract.repo.v1` | Common Core 遵守 |
| `contract.markdown.v1` | Markdown 書式 |
| `contract.surface.v1` | UI 表示 |
| `contract.workflow.v1` | workflow 書き方 |
| `contract.mnp_surface.v1` | MNP の限定使用（MNP block を使う場合） |

## `.companyos/manifest.md` 概要

| 項目 | 値 |
| --- | --- |
| spoke_id | `{target_repo_name}` |
| archetype | `archetype.{name}.v1` |
| version | `{version}` |

## expose する surface

| surface | source_pin 概要 |
| --- | --- |
|  |  |

## 関連 file

- `../../../02_contracts/00_contract_map.md`
- `../../../02_contracts/10_repo_contract.md`
- `../../../02_contracts/40_surface_contract.md`
- `../../../06_build/scaffolds/companyos_interface/manifest.md`

## 最低 acceptance

- 遵守 contract が最低 4 つ（repo / markdown / surface / workflow）
- manifest の必須項目が埋まる
- expose surface が表で読める

## 止める条件

- 必須 contract が抜けた
- 業務正本を expose しようとしている
- surface に source_pin がない

## 次の step

`06_surface_design.md` で UI への見せ方を確定する。
