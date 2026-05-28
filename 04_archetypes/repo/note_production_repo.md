---
id: archetype.note_production_repo.v1
status: active
owner: 04_archetypes
---

# note_production_repo

## 役割

note 記事を、企画・執筆・レビュー・公開・学習まで一貫して管理する target repo の archetype。

## 持つもの

- 必須 module の宣言
- 推奨 module
- 禁止 module
- 持つべき workflow
- CompanyOS に表示するもの / 表示しないもの

## 持たないもの

- 記事本文の正本（target repo 側）
- prompt 本文の正本（→ prompt_repo）
- 公開後 KPI 集計実装（→ analytics_ops extension）

---

## 目的

note 記事制作の **企画 → 執筆 → レビュー → 公開 → 学習** を一貫した SSOT として管理する。

CompanyOS UI 上では、進行中の記事カード・workflow 状態・次のアクションを表示できる。

## 必須 module

- `content_production` — 記事制作の core ループ
- `publish_pipeline` — 公開準備・公開後フォロー
- `feedback_loop`（built-in、Common Core）

## 推奨 module

- `analytics_ops` — 公開後の反応・KPI 確認

## 禁止 module

- `client_ops` — note 制作 repo は client 概念を持たない（client 案件として書く場合は別 repo に分離）

## 持つべき workflow

- `workflow.note_article_production.v1` — 記事企画から公開まで
- `workflow.research_to_content.v1` — リサーチ起点の記事化

## CompanyOS に表示するもの

- 記事カード（タイトル / 進行 status / owner / next_action）
- 公開準備状態
- source_path（記事 meta への参照）
- 月次の公開本数

## CompanyOS に表示しないもの

- 記事本文の正本
- 未公開の機密メモ
- 編集中の draft 本文
- 著者個人の感想 / feedback 原本

## archetype 固有の root（Common Core に加えて）

```text
{note-production-repo}/
├── Common Core 9 root（10_repo_contract.md 参照）
└── archetype 固有：
    ├── 02_workflows/             # workflow 本体（Markdown）
    │   ├── note_article_production.md
    │   └── research_to_content.md
    ├── 10_assets/                # 共通素材（画像・引用元）
    └── 99_publish_history/       # 公開済み記事の archive pointer
```

## quality_profile

- common quality: 全部適用（`../../07_quality/10_common_quality.md`）
- archetype quality（後段）：
  - タイトル / 本文 / 導入 / CTA / 公開準備 の各 critical gate

## 関連 contract

- `contract.repo.v1` — Common Core 遵守
- `contract.surface.v1` — note カード / workflow lens
- `contract.workflow.v1` — note_article_production の書き方
- `contract.markdown.v1` — 記事 meta / 本文の構造

## 最低 acceptance

- Common Core 9 root（+ archetype 固有 root）すべて存在
- `02_workflows/note_article_production.md` が `contract.workflow.v1` 準拠
- `.companyos/surfaces/repo_card.surface.md` が `contract.surface.v1` 準拠
- 必須 module（content_production + publish_pipeline）が `SPOKE.yml` に宣言

## 止める条件

- 記事本文を `.companyos/` 内に置こうとしている（surface_contract 違反）
- client_ops module を install しようとしている（archetype 禁止）
- workflow を YAML schema で深く割って書いている（markdown-first 違反）

## 関連ファイル

- `README.md`（archetype 一覧）
- `../00_archetype_framework.md`
- `../../02_contracts/10_repo_contract.md`
- `../../02_contracts/40_surface_contract.md`
- `../../06_build/scaffolds/companyos_interface/`
