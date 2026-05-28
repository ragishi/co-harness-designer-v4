---
id: workspace.2026-05-note-production-pilot.05_contract_design.v1
status: active
slug: 2026-05-note-production-pilot
---

# 05_contract_design.md — 連携契約

## 役割

本 pilot で `co-note-production` が遵守する contract と、target が出す `.companyos/manifest.md` の内容を確定する。

## 持つもの

- 遵守する contract 一覧（active / planned 別）
- `.companyos/manifest.md` の最低項目
- `.companyos/manifest.yml` の最低項目（YAML、機械読み）

## 持たないもの

- contract 本体の定義（→ `../../../02_contracts/`）
- surface の表示要素（→ `06_surface_design.md`）

---

## 遵守する contract（active）

| contract ID | 役割 | V4 source | target の遵守ポイント |
| --- | --- | --- | --- |
| `contract.repo.v1` | target repo の最低要件 | `co-harness-designer-v4/02_contracts/10_repo_contract.md` | Common Core 9 entries / `.companyos/` 必須要素を満たす |
| `contract.workflow.v1` | workflow の書き方 | `co-harness-designer-v4/02_contracts/20_workflow_contract.md` | 既存 `02_workflows/note_article_production.md` が frontmatter + 必須 section を満たすこと（本 pilot では確認のみ、書き換えは out of scope） |
| `contract.surface.v1` | UI 連携契約 | `co-harness-designer-v4/02_contracts/40_surface_contract.md` | `.companyos/surfaces/*.surface.md` が frontmatter / source_pin / `業務正本ではない宣言` を満たす |
| `contract.markdown.v1` | Markdown 正本構造 | `co-harness-designer-v4/02_contracts/70_markdown_contract.md` | 全 `.companyos/*.md` が標準 frontmatter + section 規約を満たす |
| `contract.mnp_surface.v1` | MNP block 使用条件 | `co-harness-designer-v4/02_contracts/80_mnp_surface_contract.md` | 本 pilot では MNP block を **書かない**（installed/ 昇格前のため）。条件のみ準拠 |

## 遵守する contract（planned stub、参照のみ）

| contract ID | status | 本 pilot での扱い |
| --- | --- | --- |
| `contract.writeback.v1` | planned stub | UI → 業務正本の直接書き戻しは行わない（contract が planned で禁止しているとおり） |
| `contract.task.v1` | planned | 本 pilot では task entity を直接扱わない |
| `contract.sync.v1` | planned | `sync/source_pin.md` の運用は本 pilot で開始するが、契約本体は後段 |

## 遵守する metric

| metric ID | 役割 | V4 source | target の遵守ポイント |
| --- | --- | --- | --- |
| `semantic.workflow_status.v1` | workflow / task の 8 enum + CompanyOS 5 enum 変換 | `co-harness-designer-v4/03_status_metrics/10_workflow_status.md` | surface 内で使う status は必ず 8 enum のいずれか。CompanyOS 投影時は 5 enum へ変換 |

---

## `.companyos/manifest.md` の最低項目（Markdown 正本）

```markdown
---
id: manifest.co-note-production.v1
status: active
owner: co-note-production
note: "CompanyOS hub への接続口宣言。業務正本ではない。"
---

# manifest.md — co-note-production の .companyos manifest

## target repo identity

| 項目 | 値 |
| --- | --- |
| spoke_id | spoke.note-production |
| archetype | archetype.note_production_repo.v1 |
| version | （target の SPOKE.yml と整合） |
| description | note 記事を企画→執筆→レビュー→公開→学習まで管理する Owner Repo |

## expose する surface

| surface | role | source_pin 概要 |
| --- | --- | --- |
| `surfaces/repo_card.surface.md` | Repo Card 表示 | `../../README.md`, `../../SPOKE.yml` |
| `surfaces/workflow_lens.surface.md` | Workflow Lens 表示 | `../../02_workflows/*.md`, `../../20_workspace/articles/*/meta.md` |
| `surfaces/member_work_lens.surface.md` | Member Work Lens 表示 | `../../20_workspace/articles/*/meta.md` |

## visibility

- 業務正本（記事本文 / draft / 未公開メモ）は **expose しない**
- expose するのは status / メタ情報 / source_pin のみ

## generated 範囲

`generated/` 配下は build パイプラインのみが書き込み可能。MVP では cache 実体ゼロ。
```

## `.companyos/manifest.yml` の最低項目（機械読み版、最小限）

```yaml
spoke_id: spoke.note-production
archetype: archetype.note_production_repo.v1
version: stable-baseline-v1
description: "note 記事を企画→執筆→レビュー→公開→学習まで管理する Owner Repo"

hub: company-os
mode: attached

surfaces:
  - id: surface.repo_card.v1
    file: surfaces/repo_card.surface.md
    role: Repo Card 表示
  - id: surface.workflow_lens.v1
    file: surfaces/workflow_lens.surface.md
    role: Workflow Lens 表示
  - id: surface.member_work_lens.v1
    file: surfaces/member_work_lens.surface.md
    role: Member Work Lens 表示

visibility:
  expose:
    - status
    - meta
    - source_pin
  do_not_expose:
    - business_canonical
    - confidential_drafts

generated:
  policy: build_pipeline_only
  location: generated/
```

## contract 違反の検出（Phase 3 適用時に Critical Gate で止める）

| Gate | 違反検出条件 |
| --- | --- |
| SSOT Gate | `.companyos/` 内に記事本文 / meta の copy が存在 |
| UI not SSOT Gate | manifest.md が「正本」を主張している |
| Markdown-first Gate | manifest.yml だけが存在し manifest.md がない |
| Source Pin Gate | surface に source_pin が欠落 |
| Contract Gate | `.companyos/manifest.md` 内に必須項目が欠落 |
| MNP Not SSOT Gate | MNP block 内に業務正本が混入 |

## 関連ファイル

- `04_directory_design.md`
- `06_surface_design.md`（各 surface の中身）
- `../../../02_contracts/`（contract 群本体）
