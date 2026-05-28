# 03_format_and_ui_policy.md — 形式 / UI ポリシー

## 役割

Markdown / YAML / JSON / HTML / MNP の使い分けを固定する。

## 持つもの

- 各形式の用途
- 正本にしてよい形式 / してはいけない形式
- YAML を使ってよい箇所
- 形式違反の例（止める条件）

## 持たないもの

- 個別 contract のスキーマ詳細（→ `../02_contracts/`）
- 個別 metric の計算式（→ `../03_status_metrics/`）

---

## 原則

```text
正本は Markdown を基本にする
YAML は最小限の索引・manifest・status mapping に限定する
JSON は原則 generated cache であり、正本にしない
HTML / UI は表示であり、正本にしない
MNP notation は Surface 中間記法であり、業務正本にしない
同じ情報を 2 箇所に書かない
```

## 各形式の扱い

| 形式 | 用途 | 正本にしてよいか |
| --- | --- | :---: |
| Markdown | 思想・契約・設計・workflow・feedback・learning・glossary | ◎ |
| Markdown + YAML frontmatter | id / status / owner などの最低限機械情報 | ◎ |
| YAML | SPOKE.yml / manifest.yml / index / status mapping / read set | △（最小限なら可） |
| JSON | UI が読む generated cache | × |
| HTML | 表示・操作画面 | × |
| MNP notation | Surface 状態の中間記法 | × （Markdown 正本から生成・参照する） |

## YAML を使ってよい箇所（MVP では限定列挙）

- `SPOKE.yml`（V4 root）
- 各 target repo の `SPOKE.yml`
- 各 target repo の `.companyos/manifest.yml`
- `06_build/scaffolds/companyos_interface/manifest.yml.example`

これ以外で YAML を新規追加したい場合は `04_decision_rules.md` の DRR 5 質問を通す。

## Markdown 正本の構造

`../02_contracts/70_markdown_contract.md` を参照。

最低限：

```markdown
---
id: {entity_or_contract_id}.{version}
status: active | draft | deprecated
owner: {tier_or_team}
---

# {title}

## 0. Executive Summary
## 0.5 Operational Card（任意）
## 1. 役割
## 2. 持つもの
## 3. 持たないもの
...
```

## MNP の位置づけ

MNP は Surface 状態を AI が編集しやすい中間記法。

- 採用：Topology / Workflow Lens / Member Work Lens / Surface 表示
- 非採用：設計思想・契約本文・SSOT・feedback・learning・業務正本

詳細は `../02_contracts/80_mnp_surface_contract.md`。

## 止める条件

- UI 内に task 本体が直書きされている
- generated JSON を人間が編集している
- Markdown 正本なしで YAML だけで意味を定義している
- MNP に業務正本（記事本文、台本、納品物）が入っている
- MNP から業務正本へ直接書き戻している

## 関連ファイル

- `01_principles.md`（P0, P2）
- `02_ssot_authority_map.md`
- `../02_contracts/70_markdown_contract.md`
- `../02_contracts/80_mnp_surface_contract.md`
- `../07_quality/30_critical_gates.md`

## 最低 acceptance

- 5 形式（Markdown / YAML / JSON / HTML / MNP）の扱いが表で読める
- 止める条件が 4 つ以上書かれている
- YAML を使ってよい箇所が限定列挙されている

## 関連 root

- `../02_contracts/`
- `../07_quality/`
