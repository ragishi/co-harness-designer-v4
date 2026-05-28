---
id: workspace.{slug}.04_directory_design.v1
status: draft
slug: "{YYYY-MM-{slug}}"
---

# 04_directory_design.md — ディレクトリ構成

## 役割

target repo の **ディレクトリツリー** を確定する。

## 持つもの

- Common Core + archetype 固有 root のツリー
- 各 root の役割（一言）

## 持たないもの

- 個別 file の本文
- contract（→ `05_contract_design.md`）

## ツリー

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
├── .companyos/
└── archetype 固有：
    └── ...
```

## 各 root の役割

| root | 役割 |
| --- | --- |
| `00_foundation/` | target repo の憲法 |
| `20_workspace/` | 作業中 |
| ... |  |

## DRR 5 質問の通過確認

- [ ] Q1: 既存 root では表現できないか
- [ ] Q2: 観察 3 回以上の根拠
- [ ] Q3: 3 行で失敗を articulate
- [ ] Q4: cost < value
- [ ] Q5: 運用粒度内

## 関連 file

- `../../../04_archetypes/repo/{archetype}.md`
- `../../../02_contracts/10_repo_contract.md`

## 最低 acceptance

- Common Core 9 entries すべて
- archetype 固有 root が必要分のみ
- DRR 5 質問通過

## 止める条件

- Common Core が欠けた
- archetype が要求していない root が追加された
- DRR を通さず root が追加された

## 次の step

`05_contract_design.md` で連携契約を設計する。
