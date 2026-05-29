# co-harness-designer-v4

**stable-baseline-v4-mvp** / Repository Harness Factory

---

## 30 秒 TL;DR

Harness Designer V4 は、CompanyOS に接続できる**目的別 Repo** を **Markdown-first** で設計・生成・検証・改善するための **Repository Harness Factory** である。

V4 は新しい目的別 Repo を作るだけでなく、**既存 Repo の診断・改修・CompanyOS 接続追加・V4 自身の改善**も同格に扱う。依頼を受けたら、最初に作業モード（operation_mode）を決める（→ `00_foundation/05_operating_modes.md`）。

```text
依頼を受ける
  ↓
operation_mode を決める
  ↓
新規Repo設計 / 既存Repo診断 / 既存Repo改修 / CompanyOS接続追加 / V4自身の改善
  ↓
mode 別の read_set を読み、20_workspace で設計し、必要なら 21_outputs へ出す
  ↓
target repo を触る場合は明示承認のみ → 30_feedback へ戻す
```

作る対象と価値の流れ:

```text
目的別 Repo を作る
  ↓
note 制作 / client 案件 / SNS 運用 / YouTube 運用 / project 管理 / workflow 制作

各 Repo に正本を持たせる
  ↓
Markdown 中心で、人間も AI も読める

CompanyOS UI に安全に投影する
  ↓
カード・レンズ・ワークフローとして表示

使うほど改善される
  ↓
30_feedback → 31_learning → accepted pattern → core 反映
```

---

## 何を作る Repo か

V4 が産む **archetype（目的別 Repo 型）**：

- `note_production_repo` — note 記事制作
- `client_repo` — クライアント案件管理
- `project_progress_repo` — プロジェクト進捗
- `sns_operations_repo` — SNS 運用
- `youtube_ops_repo` — YouTube 運用
- `workflow_ops_repo` — workflow 設計・運用
- `prompt_repo` — Prompt 正本管理
- `design_system_repo` — UI token / component

MVP では `note_production_repo` と `client_repo` の 2 つから検証する。

---

## 絶対ルール

| # | ルール |
| --- | --- |
| 1 | **Markdown が正本** |
| 2 | **UI is not SSOT**（HTML / 画面は投影先、正本ではない） |
| 3 | **JSON is generated cache**（正本にしない） |
| 4 | **YAML is minimal**（manifest / index のみ） |
| 5 | **`30_feedback/` と `31_learning/` は分離**（V3 継承） |
| 6 | **MNP は Surface 用 optional extension のみ**（全面採用しない） |

---

## 全体構造（16 root）

```text
co-harness-designer-v4/
├── 00_foundation/      設計の憲法
├── 01_meaning_model/   意味モデル (オントロジー相当)
├── 02_contracts/       連携の約束
├── 03_status_metrics/  状態・指標 (セマンティック相当)
├── 04_archetypes/      目的別 Repo 原型 (★ V4 の中核)
├── 05_read_sets/       AI / UI 読書セット
├── 06_build/           scaffold / exporter
├── 07_quality/         品質ゲート
│
├── 10_references/      外部参考
├── 11_connect/         CompanyOS / 外部 Repo 接続
│
├── 20_workspace/       作業中
├── 21_outputs/         完成物
│
├── 30_feedback/        生の観測 (V3 継承)
├── 31_learning/        抽象化された学び (V3 継承)
│
├── 40_extensions/      後付け拡張
└── 90_archive/         退役
```

---

## 最初に読む順番

| # | file | 目的 |
| --- | --- | --- |
| 1 | `README.md` | V4 全体像（このファイル） |
| 2 | `SPOKE.yml` | 接続契約 |
| 3 | `CLAUDE.md` | AI 起動 router |
| 4 | `CLAUDE.gate.md` | 完了前検査 |
| 5 | `00_foundation/README.md` | 憲法 root の地図 |
| 6 | `00_foundation/00_purpose.md` | V4 の目的 |
| 7 | `00_foundation/02_ssot_authority_map.md` | 3 所有者地図 |
| 8 | `04_archetypes/README.md` | V4 の中核 |
| 9 | `02_contracts/README.md` | 連携の約束 |
| 10 | `07_quality/README.md` | 品質ゲート |

---

## 接続情報

- **hub**: company-os
- **predecessor**: co-harness-design-v3（successor_created / not_archived）
- **archetype**: connected_capability
- **mode**: attached

---

## MVP scope について

このリポジトリは **MVP 構成**で開始している。残りの archetype / exporter / writeback / automation は使いながら段階的に追加する。完成形を一気に作らないことが原則。

MVP 範囲は `00_foundation/04_decision_rules.md` の Section "MVP boundaries" を参照。

---

## license / visibility

- visibility: public
- maintainer: ragishi
