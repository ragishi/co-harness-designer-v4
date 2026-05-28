# 04_archetypes/repo/ — repo archetype 一覧

## 役割

8 つの目的別 Repo archetype の定義を置く。

## archetype 一覧

| archetype | 目的 | MVP |
| --- | --- | :---: |
| `note_production_repo` | note 記事制作 | ✓ |
| `client_repo` | クライアント案件管理 | ✓ |
| `project_progress_repo` | プロジェクト進捗 | — 後段 |
| `sns_operations_repo` | SNS 運用 | — 後段 |
| `youtube_ops_repo` | YouTube 運用 | — 後段 |
| `workflow_ops_repo` | workflow 設計・運用 | — 後段 |
| `prompt_repo` | Prompt 正本管理 | — 後段 |
| `design_system_repo` | UI token / component | — 後段 |

MVP では 2 archetype のみ。残りは使いながら追加（DRR 5 質問を通す）。

## 命名規則

- ファイル名は `{purpose}_repo.md`
- frontmatter id は `archetype.{purpose}_repo.v1`

## 構造（各 archetype が持つ section）

`../00_archetype_framework.md` の標準構造に従う：

- 目的
- 必須 module
- 推奨 module
- 禁止 module
- 持つべき workflow
- CompanyOS に表示するもの / 表示しないもの
- 関連 contract / quality

## 最低 acceptance

- 全 archetype が `id: archetype.{name}.v1` の frontmatter を持つ
- 全 archetype が「必須 module」「禁止 module」を明示する
- 全 archetype が「表示するもの / 表示しないもの」を明示する

## 関連ファイル

- `../00_archetype_framework.md`
- `../../02_contracts/10_repo_contract.md`
- `../../40_extensions/`
