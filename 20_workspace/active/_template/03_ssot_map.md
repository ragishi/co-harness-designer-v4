---
id: workspace.{slug}.03_ssot_map.v1
status: draft
slug: "{YYYY-MM-{slug}}"
---

# 03_ssot_map.md — 正本の置き場所

## 役割

target repo の **正本住所地図** を作る。3 所有者（company-os / V4 / target）で正本を割り振る。

## 持つもの

- 何の正本がどこにあるか
- 一方向の参照関係

## 持たないもの

- 業務正本本体
- 接続実装（→ `05_contract_design.md`）

## 正本住所表

| 何 | 所有者 | 場所 |
| --- | --- | --- |
| status enum | company-os | `task_source_contract.yml`（ID 参照） |
| projection target | company-os | `projection_registry.yml`（ID 参照） |
| archetype 定義 | V4 | `../../../04_archetypes/repo/{archetype}.md` |
| workflow 本文 | target | `{target-repo}/02_workflows/*.md` |
| instance 状態 | target | `{target-repo}/20_workspace/active/*/meta.md` |
| 業務正本（記事本文等） | target | `{target-repo}/20_workspace/active/*/` |
| `.companyos/manifest.md` | target | `{target-repo}/.companyos/manifest.md` |
| `.companyos/surfaces/*` | target | 同上 |

## 参照方向

```text
target ──depends_on──> V4 archetype + contracts
V4    ──references──> company-os enums + contracts
（書き戻し / 上書きは禁止）
```

## 関連 file

- `../../../00_foundation/02_ssot_authority_map.md`
- `../../../02_contracts/00_contract_map.md`

## 最低 acceptance

- 正本住所表に最低 5 項目あり
- 一方向の参照関係が明示
- company-os の正本を V4 / target が複製していない

## 止める条件

- 同じ正本が 2 箇所に置かれた
- 参照方向が双方向になった
- 業務正本本体が `.companyos/` に置かれた

## 次の step

`04_directory_design.md` でディレクトリ構成を設計する。
