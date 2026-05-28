---
id: archetype.client_repo.v1
status: active
owner: 04_archetypes
---

# client_repo

## 役割

クライアント案件を、依頼・契約・WBS・成果物・納品・振り返りまで管理する target repo の archetype。

## 持つもの

- 必須 module の宣言
- 推奨 module
- 禁止 module
- 持つべき workflow
- CompanyOS に表示するもの / 表示しないもの

## 持たないもの

- 納品物の本文（target repo 側）
- prompt 本文の正本（→ prompt_repo）
- 公開系運用（content_production / publish_pipeline は note / SNS / YouTube 側）

---

## 目的

クライアント案件の **依頼 → 契約 → WBS → 制作 → レビュー → 納品 → 振り返り** を一貫した SSOT として管理する。

CompanyOS UI 上では、案件ごとの進行 status / 次のアクション / 期限 / 承認状況を表示できる。

## 必須 module

- `client_ops` — クライアント別管理の core
- `project_management` — WBS / 進捗 / milestone
- `feedback_loop`（built-in、Common Core）

## 推奨 module

- `automation_pack` — 案件横断の自動化（reminder / status 更新）

## 禁止 module

- `content_production` — 制作物は target が note / YouTube / SNS なら別 repo（client_repo は案件管理の正本のみ）

## 持つべき workflow

- `workflow.client_workflow.v1` — クライアント案件の標準フロー
- `workflow.project_management.v1` — WBS と milestone 運用

## CompanyOS に表示するもの

- 案件カード（クライアント名 / 案件名 / 進行 status / next_action / due）
- WBS（task 別 status）
- 承認 / 納品状態
- source_path（案件 meta への参照）

## CompanyOS に表示しないもの

- 納品物本体（契約上の機密含む）
- クライアント個別の機密メモ
- 報酬・請求金額の詳細（必要時は別 surface に隔離）
- 内部 review の生コメント

## archetype 固有の root（Common Core に加えて）

```text
{client-repo}/
├── Common Core 9 root（10_repo_contract.md 参照）
└── archetype 固有：
    ├── 02_workflows/
    │   ├── client_workflow.md
    │   └── project_management.md
    ├── 10_clients/               # クライアント別フォルダ
    │   └── {client_slug}/
    │       ├── meta.md
    │       ├── projects/{project_slug}/
    │       └── archive/
    └── 99_invoices/              # 請求書 archive（visibility 制御）
```

## quality_profile

- common quality: 全部適用
- archetype quality（後段）：
  - WBS / 依存関係 / 期限 / 担当者 / 承認履歴 の critical gate

## 関連 contract

- `contract.repo.v1` — Common Core 遵守
- `contract.surface.v1` — client カード / WBS lens
- `contract.workflow.v1` — client_workflow / project_management の書き方
- `contract.markdown.v1` — 案件 meta の構造

## 最低 acceptance

- Common Core 9 root（+ archetype 固有 root）すべて存在
- `10_clients/{slug}/meta.md` が `contract.markdown.v1` 準拠
- `.companyos/surfaces/repo_card.surface.md` に案件カード surface あり
- 必須 module（client_ops + project_management）が `SPOKE.yml` に宣言
- 機密情報（請求金額 / 納品物本体）が `.companyos/` 外に置かれている

## 止める条件

- 納品物本体を `.companyos/` 内に置こうとしている（surface_contract 違反）
- content_production module を install しようとしている（archetype 禁止）
- クライアント機密が source_pin なしで CompanyOS に expose されている

## 関連ファイル

- `README.md`（archetype 一覧）
- `../00_archetype_framework.md`
- `../../02_contracts/10_repo_contract.md`
- `../../02_contracts/40_surface_contract.md`
- `../../06_build/scaffolds/companyos_interface/`
