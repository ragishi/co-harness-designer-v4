---
id: workspace.2026-05-note-production-pilot.04_directory_design.v1
status: active
slug: 2026-05-note-production-pilot
---

# 04_directory_design.md — ディレクトリ構成

## 役割

`co-note-production` の **ディレクトリツリー**（Common Core + archetype 固有 + `.companyos/`）を本 pilot 用に確定する。

## 持つもの

- Common Core 9 entries（再掲）
- note_production_repo 固有 root
- `.companyos/` の 10 file 内訳（Phase 3 で実装）
- 既存 root を壊さない設計

## 持たないもの

- 各 file の中身（→ 05, 06）
- 実装手順（→ 08）

---

## 全体ツリー（Phase 3 完了後の `co-note-production`）

```text
co-note-production/
│
├── README.md                              # root file (Common Core)
├── SPOKE.yml                              # root file (Common Core)
├── CLAUDE.md                              # AI 起動 router（V4 から雛形）
├── CLAUDE.gate.md                         # 完了前検査（V4 から雛形）
│
├── 00_foundation/                         # Common Core
├── 20_workspace/                          # Common Core（業務正本の一部）
│   └── articles/{slug}/
│       ├── meta.md                        # ★ 記事 meta（業務正本）
│       └── draft.md                       # ★ 記事本文（業務正本）
├── 21_outputs/                            # Common Core
├── 30_feedback/                           # Common Core
├── 31_learning/                           # Common Core
├── 90_archive/                            # Common Core
│
├── 02_workflows/                          # archetype 固有
│   ├── note_article_production.md         # ★ workflow 正本
│   └── research_to_content.md
├── 10_assets/                             # archetype 固有（共通素材）
├── 99_publish_history/                    # archetype 固有
│
└── .companyos/                            # ★★ 本 pilot の中心 ★★
    ├── README.md                          # 接続口宣言（正本ではない）
    ├── manifest.md                        # Markdown 正本
    ├── manifest.yml                       # 機械読み版（最小限）
    │
    ├── surfaces/                          # UI 表示用 surface 定義
    │   ├── repo_card.surface.md           # ★ Repo Card 用
    │   ├── workflow_lens.surface.md       # ★ Workflow Lens 用
    │   └── member_work_lens.surface.md    # ★ Member Work Lens 用
    │
    ├── sync/                              # source_pin / freshness / generated_from
    │   ├── source_pin.md                  # ★ 全 surface の参照元
    │   ├── freshness.md                   # 鮮度（last_synced_at）
    │   └── generated_from.md              # generated 物の出自
    │
    └── generated/                         # 再生成可能 cache（正本ではない）
        └── README.md                      # 雛形 README のみ、cache 実体は MVP では空
```

## Common Core 9 entries の確認（本 pilot の最低 acceptance）

| # | entry | type | 既存 / 新規 |
| --- | --- | --- | --- |
| 1 | `README.md` | root file | 既存 |
| 2 | `SPOKE.yml` | root file | 既存（archetype 宣言を追記） |
| 3 | `00_foundation/` | directory | 既存 |
| 4 | `20_workspace/` | directory | 既存 |
| 5 | `21_outputs/` | directory | 既存 |
| 6 | `30_feedback/` | directory | 既存 |
| 7 | `31_learning/` | directory | 既存 |
| 8 | `90_archive/` | directory | 既存 |
| 9 | `.companyos/` | directory | **新規（本 pilot で追加）** |

→ Phase 3 では `.companyos/` を 1 つ追加するだけで Common Core を 9 entries にする。

## `.companyos/` 内訳（Phase 3 で作る 10 file）

| # | path | 形式 | 役割 |
| --- | --- | --- | --- |
| 1 | `.companyos/README.md` | md | 接続口宣言（「正本ではない」明記） |
| 2 | `.companyos/manifest.md` | md | Markdown 正本 |
| 3 | `.companyos/manifest.yml` | yml | 機械読み版（最小限） |
| 4 | `.companyos/surfaces/repo_card.surface.md` | md | Repo Card surface |
| 5 | `.companyos/surfaces/workflow_lens.surface.md` | md | Workflow Lens surface |
| 6 | `.companyos/surfaces/member_work_lens.surface.md` | md | Member Work Lens surface |
| 7 | `.companyos/sync/source_pin.md` | md | source_pin 一覧 |
| 8 | `.companyos/sync/freshness.md` | md | 鮮度規約 |
| 9 | `.companyos/sync/generated_from.md` | md | generated 物の出自記録 |
| 10 | `.companyos/generated/README.md` | md | 「再生成可能 cache、手動編集禁止」明記 |

すべて Markdown 中心。`manifest.yml` のみが YAML（manifest.md からの機械読み変換、最小限）。

## 既存 root を壊さない設計（重要）

- 既存の `02_workflows/` / `10_assets/` / `99_publish_history/` は **触らない**
- `20_workspace/articles/` の記事 / meta は **コピーも移動もしない**
- `.companyos/` は新規 root として追加するだけ
- `SPOKE.yml` には archetype 宣言を **追記**（既存項目は維持）

## 関連ファイル

- `03_ssot_map.md`（この dir 構造の SSOT 根拠）
- `05_contract_design.md`（各 dir で遵守する contract）
- `../../../02_contracts/10_repo_contract.md`（Common Core 9 entries 仕様）
- `../../../06_build/scaffolds/companyos_interface/`（`.companyos/` 雛形 source）
