# 10_repo_contract.md — target repo の最低要件

## 役割

V4 が産む全 target repo が **最低限持つもの** を定義する。

## 持つもの

- target repo の必須 root list（Common Core）
- 必須 root files
- `.companyos/` interface の必須要素
- SPOKE.yml の必須項目

## 持たないもの

- archetype 固有の構造（→ `../04_archetypes/repo/{archetype}.md`）
- 個別 workflow（→ target repo 側）

---

## Common Core（全 target repo が必ず持つ root）

```text
{target-repo}/
├── README.md
├── SPOKE.yml
├── 00_foundation/
├── 20_workspace/
├── 21_outputs/
├── 30_feedback/
├── 31_learning/
├── 90_archive/
└── .companyos/
```

archetype 固有の root（`01_meaning_model/` や `02_contracts/` 相当）は V4 から伝播される blueprint で決まる。target は **必ず Common Core を持つ**。

## 必須 root files

| file | 役割 |
| --- | --- |
| `README.md` | repo の入口 |
| `SPOKE.yml` | CompanyOS hub への接続契約 |
| `CLAUDE.md` | AI 起動 router（V4 から雛形を伝播） |
| `CLAUDE.gate.md` | 完了前検査 |

## SPOKE.yml の必須項目

```yaml
spoke_id: {target_repo_name}
version: {semver_or_baseline}
description: "..."
connection:
  hub: company-os
  mode: attached
archetype: {one_of_v4_archetypes}
mvp_archetypes:
  - {archetype_id}
```

## `.companyos/` interface 必須要素

```text
{target-repo}/.companyos/
├── README.md         # 接続口の説明
├── manifest.md       # 何を expose するか（Markdown 正本）
├── manifest.yml      # manifest の機械読み版（最小限）
├── surfaces/         # UI 表示用 Surface 定義
│   └── *.surface.md
├── sync/             # 何から生成されたか
│   ├── source_pin.md
│   ├── freshness.md
│   └── generated_from.md
└── generated/        # 再生成可能 cache
    └── README.md
```

詳細雛形は `../06_build/scaffolds/companyos_interface/` を参照。

## `.companyos/` に置いてよいもの / 置いてはいけないもの

| 置いてよい | 置いてはいけない |
| --- | --- |
| manifest | 業務正本（記事本文、台本、納品物） |
| surface 定義 | WBS 本体 |
| source_pin | クライアント納品物 |
| freshness | feedback 原本 |
| generated cache | learning 本文 |
| MNP block（`80_mnp_surface_contract.md` 準拠） | Prompt 正本 |

業務正本は target repo の通常 directory（`20_workspace/`, `21_outputs/`, `02_workflows/` など）に置く。

## 最低 acceptance

- Common Core 9 root（README / SPOKE.yml / 8 root）すべて存在
- SPOKE.yml に 6 必須項目すべてあり
- `.companyos/` の 4 sub-dir（surfaces / sync / generated）+ manifest が存在
- `.companyos/README.md` に「接続口であり正本ではない」明記
- archetype 固有 root（archetype に従う）が存在

## 止める条件

- Common Core の root が欠けている
- `.companyos/` に業務正本がコピーされている
- SPOKE.yml が JSON で書かれている
- `.companyos/manifest.md`（Markdown 正本）が欠けている

## 関連ファイル

- `40_surface_contract.md`
- `70_markdown_contract.md`
- `80_mnp_surface_contract.md`
- `../04_archetypes/00_archetype_framework.md`
- `../06_build/scaffolds/companyos_interface/`
