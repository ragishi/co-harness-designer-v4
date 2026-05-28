---
id: workspace.2026-05-note-production-pilot.02_archetype_choice.v1
status: active
slug: 2026-05-note-production-pilot
---

# 02_archetype_choice.md — 使う archetype

## 役割

この pilot 設計作業で使う / 産む **archetype を選ぶ**、選択根拠を明示する。

## 持つもの

- 選んだ archetype（ID）
- 採用根拠
- 候補比較（採用 / 不採用 / 後段）

## 持たないもの

- archetype 本体の定義（→ `../../../04_archetypes/repo/note_production_repo.md`）
- 必須 module の実装（→ `../../../40_extensions/`、MVP では未配置）

---

## 採用 archetype

| 項目 | 値 |
| --- | --- |
| ID | `archetype.note_production_repo.v1` |
| 場所 | `../../../04_archetypes/repo/note_production_repo.md` |
| status | active（MVP archetype 2 つのうちの 1 つ） |

## 採用根拠

1. **note 制作 = 一番境界が分かりやすい**
   - 記事本文 / meta / workflow / 公開状態 / source_pin / CompanyOS 表示の **役割境界**が明瞭
   - 業務正本（記事本文）と投影（surface）の分離が直感的
   - 「UI に出すべき情報」と「出してはいけない情報」の判定が楽
2. **content_production + publish_pipeline の最小 module 組合せ**
   - 必須 module 2 つ（+ built-in 1）で動かせる
   - client_ops のような複雑な権限境界がない
   - `analytics_ops` は推奨で、MVP では skip 可能
3. **将来の archetype 追加（YouTube / SNS）も同じ Owner Repo 系列**
   - `entity.owner_repo.v1` のサブセット
   - note pilot で得た知見が YouTube / SNS にも転用可能
4. **既存 repo `co-note-production` が存在し、構造が note archetype の前提と整合**
   - V4 設計を直接当てやすい

## 候補比較（本 pilot で選ばれなかった archetype）

| 候補 | 採否 | 理由 |
| --- | :---: | --- |
| `archetype.note_production_repo.v1` | **採用** | 上記根拠 |
| `archetype.client_repo.v1` | 次回候補 | 機密 / 契約 / WBS が絡み、最初の pilot としては複雑度が高い |
| `archetype.project_progress_repo.v1` | 後段 | archetype 自体が未実装（MVP 範囲外） |
| `archetype.youtube_ops_repo.v1` | 後段 | archetype 自体が未実装、Owner Repo 系列で note 後継 |
| `archetype.sns_operations_repo.v1` | 後段 | archetype 自体が未実装、Owner Repo 系列で note 後継 |
| `archetype.workflow_ops_repo.v1` | 後段 | archetype 自体が未実装 |
| `archetype.prompt_repo.v1` | 後段 | archetype 自体が未実装、MNP installed/ 昇格と相関 |
| `archetype.design_system_repo.v1` | 後段 | archetype 自体が未実装、優先度低 |

## 採用 archetype の制約（再掲、本 pilot で必ず守る）

### 必須 module（target SPOKE.yml に宣言）

- `content_production`
- `publish_pipeline`
- `feedback_loop`（Common Core built-in、明示宣言不要）

### 推奨 module

- `analytics_ops`（本 pilot では skip、Phase 4 以降で追加検討）

### 禁止 module

- `client_ops`（archetype mismatch、絶対に install しない）

### 持つべき workflow

- `workflow.note_article_production.v1`
- `workflow.research_to_content.v1`

### CompanyOS に表示するもの

- 記事カード（タイトル / 進行 status / owner / next_action）
- 公開準備状態
- source_path（記事 meta への参照）
- 月次の公開本数

### CompanyOS に表示しないもの

- **記事本文の正本**
- 未公開の機密メモ
- 編集中の draft 本文
- 著者個人の感想 / feedback 原本

## 関連ファイル

- `01_scope.md`（in/out スコープと整合）
- `../../../04_archetypes/repo/note_production_repo.md`（archetype 本体）
- `../../../04_archetypes/00_archetype_framework.md`（archetype 共通 framework）
- `../../../40_extensions/00_extension_policy.md`（module = extension の関係）
