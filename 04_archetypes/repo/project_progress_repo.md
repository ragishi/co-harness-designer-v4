---
id: archetype.project_progress_repo.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# project_progress_repo — プロジェクト進捗管理の archetype

## 役割

WBS・進捗・milestone を中心に、プロジェクトの進行を一貫した SSOT として管理する target repo の archetype。client_repo が「クライアント案件」を主語にするのに対し、本 archetype は「プロジェクトそのものの進捗」を主語にする。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。進捗管理専用の target repo を起こす需要が観測され、DRR 5 質問を通過したときに本格詳細化する。

## 持つもの

- WBS / milestone / 進捗ログの SSOT
- 進捗の可視化（進捗カード / milestone / 遅延）
- 必須 / 推奨 / 禁止 module 構成（下記で詳細化）
- project_management workflow への参照

## 持たないもの

- 制作物の正本（content_production は禁止、note / SNS / YouTube 側）
- client 案件を主語にすること（それは client_repo）
- WBS 本体の正本を `.companyos/` に置くこと

## 目的（後段で詳細化）

WBS / milestone / 進捗ログを管理し、CompanyOS UI 上で進捗カード・milestone・遅延を可視化する。詳細な section 内容は後段で `../00_archetype_framework.md` の標準構造に沿って詳細化する。

## 必須 module（後段で詳細化）

- `project_management` — WBS / 進捗 / milestone の core
- `feedback_loop`（built-in、Common Core）

## 推奨 module（後段で詳細化）

- `automation_pack` — status 集計・reminder の自動化（運用が固まってから）

## 禁止 module（後段で詳細化）

- `content_production` — 制作物は note / YouTube / SNS 側の repo に分離

## 持つべき workflow（後段で詳細化）

- `workflow.project_management.v1` — WBS と milestone 運用

## CompanyOS に表示するもの（後段で詳細化）

- 進捗カード（プロジェクト名 / 進行 status / next_action / due）
- milestone と達成状況
- source_path（WBS meta への参照）

## CompanyOS に表示しないもの（後段で詳細化）

- WBS 本体の正本（target repo 側）
- 内部 review の生コメント

## archetype 固有の root（後段で詳細化）

Common Core 9 entries（`../../02_contracts/10_repo_contract.md` 参照）に加え、`02_workflows/` と進捗管理用フォルダを持つ見込み。具体構造は後段で確定する。

## quality_profile（後段で詳細化）

- common quality: 全部適用（`../../07_quality/10_common_quality.md`）
- archetype quality（後段）：WBS / 依存関係 / 期限 / 担当者 の critical gate

## 関連 contract（後段で詳細化）

- `contract.repo.v1` — Common Core 遵守
- `contract.surface.v1` — 進捗カード / milestone lens
- `contract.workflow.v1` — project_management の書き方

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- client_repo（案件主語）との役割差が読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- client_repo / workflow_ops_repo と役割が重複したまま放置する

## 関連ファイル

- `README.md`
- `client_repo.md`
- `../00_archetype_framework.md`
- `../workflows/project_management.md`
- `../../01_meaning_model/10_entities.md`
