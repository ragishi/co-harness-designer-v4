# 20_workflow_contract.md — workflow の書き方

## 役割

target repo 内 / archetype 内で workflow をどう Markdown で書くかを定義する。

## 持つもの

- workflow Markdown の標準構造
- 必須 section
- ID 参照ルール
- Operational Card テンプレ

## 持たないもの

- 個別 workflow の本文（→ archetype 側 / target repo 側）
- task / phase の意味（→ `../01_meaning_model/10_entities.md`）
- status enum（→ `../03_status_metrics/10_workflow_status.md`）

## Workflow Markdown の構造

```markdown
---
id: workflow.{name}.{version}
status: active | draft | deprecated
owner: {tier_or_archetype}
---

# {workflow_title}

## 0. Executive Summary
何を達成する workflow か（3-5 行）。

## 0.5 Operational Card（実行カード）

| 項目 | 内容 |
| --- | --- |
| 入力 | ... |
| 使う場面 | ... |
| 手順 | 1. → 2. → 3. |
| 出力 | ... |
| 最低 acceptance | ... |
| 止める条件 | ... |
| 詳細を見る時 | ... |

## 1. Goal + Triggers
## 2. Phases
## 3. Input / Output
## 4. Gates
## 5. Failure Modes / Stop Conditions
```

V3 の Operational Card 文化を継承。

## ID 参照ルール

workflow は以下を **ID 参照**する（コピーしない）：

- entity 定義 → `../01_meaning_model/10_entities.md` の §{n}
- contract → `00_contract_map.md` 経由
- status enum → `../03_status_metrics/10_workflow_status.md`

定義本文を workflow の中に直書きしてはいけない（drift 防止）。

## 最低 acceptance

- 必須 section（0 / 0.5 / 1 / 2 / 3）がある
- frontmatter に id / status / owner がある
- ID 参照で済む箇所に定義本文が直書きされていない

## 止める条件

- workflow に entity 定義本体が混入した
- workflow に metric 計算式が直書きされた
- status が `../03_status_metrics/10_workflow_status.md` の enum 外を使っている
- Operational Card が欠けている主要 workflow

## 関連ファイル

- `00_contract_map.md`
- `70_markdown_contract.md`
- `../01_meaning_model/10_entities.md`
- `../03_status_metrics/10_workflow_status.md`
