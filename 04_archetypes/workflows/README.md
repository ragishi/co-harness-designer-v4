---
id: archetype.workflows.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 04_archetypes/workflows/ — workflow archetype 入口

## 役割

archetype が参照する**共通 workflow 型**の定義を置く folder。ここに置くのは「workflow の型（Phase の連続・入出力・gate の骨格）」であり、実際の workflow 業務正本は target repo 側の `02_workflows/` に置く。型と正本を分離するための入口。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 folder は MVP ではまだ使わない（active 化しない）。各 workflow を archetype が実際に参照する段階で、対応する型を本格詳細化する。

## このフォルダが持つもの

| file | 役割 | status |
| --- | --- | --- |
| `README.md` | workflow archetype 入口（本 file） | 後段 |
| `project_management.md` | 進捗管理 workflow 型 | 後段 |
| `client_workflow.md` | クライアント案件 workflow 型 | 後段 |
| `note_article_production.md` | note 記事制作 workflow 型 | 後段 |
| `youtube_video_production.md` | YouTube 動画制作 workflow 型 | 後段 |
| `sns_post_production.md` | SNS 投稿制作 workflow 型 | 後段 |
| `research_to_content.md` | リサーチ起点の記事化 workflow 型 | 後段 |

## このフォルダが持たないもの

- workflow の業務正本（→ target repo 側の `02_workflows/`）
- workflow_contract の本文（→ `../../02_contracts/20_workflow_contract.md`）
- 個別 archetype の定義（→ `../repo/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- 「型はここ、業務正本は target repo」の分離が読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- workflow 業務正本を本 folder に置く前提を書く

## 関連ファイル

- `../repo/`
- `../../02_contracts/20_workflow_contract.md`
- `../../01_meaning_model/10_entities.md`
