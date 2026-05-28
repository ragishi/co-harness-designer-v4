# 00_purpose.md — V4 の目的

## 役割

Harness Designer V4 が何のために存在するかを宣言する。

## 持つもの

- V4 のミッション
- V4 が作る対象
- V4 が作らない対象
- V4 と V3 の関係

## 持たないもの

- 具体 workflow
- 個別 metric
- 個別 entity 定義

---

## ミッション

```text
Harness Designer V4
=
CompanyOS に接続できる目的別 Repo を
Markdown-first で設計・生成・検証・改善するための
Repository Harness Factory
```

やさしく言うと、

> **note 制作、client 案件、SNS 運用、YouTube 運用、project 管理、workflow 制作などの目的別 Repo を、同じ思想・同じ品質・同じ CompanyOS 接続方式で作れるようにする設計工場。**

## V4 が作る対象（archetype）

- `note_production_repo` — note 記事制作
- `client_repo` — クライアント案件管理
- `project_progress_repo` — プロジェクト進捗
- `sns_operations_repo` — SNS 運用
- `youtube_ops_repo` — YouTube 運用
- `workflow_ops_repo` — workflow 設計・運用
- `prompt_repo` — Prompt 正本管理
- `design_system_repo` — UI token / component

MVP では `note_production_repo` と `client_repo` の 2 つから検証する。

## V4 が作らない対象

- CompanyOS 本体（hub の所有物）
- 投稿本文の正本（target repo の所有物）
- YouTube 台本の正本（target repo の所有物）
- UI そのものの正本（company-os の所有物）
- JSON 中心の管理システム
- target Repo の業務成果物

## V3 との関係

- V3 (`co-harness-design-v3`) は `successor_created_not_archived` 状態で残す
- V4 は V3 の以下を継承する：
  - 5-tier 思想（WHY / WHEN+ORDER / WHAT GOOD / FOR WHO / HOW）
  - 改善ループ（`30_feedback/` と `31_learning/` の分離）
  - DRR 5 質問 / L0–L4 permanence / 6-step migration package
  - per-tier `feedback.md`
  - signal registry の lifecycle（再発 ≥ 3 / 冷却 ≥ 7 日 / grader / boundary check）
- V4 が新たに加えるもの：
  - archetype の中核化（`04_archetypes/` を V4 の心臓に）
  - `.companyos/` interface（target 側の接続口）
  - meaning_model / contracts / status_metrics / read_sets の独立 root 化（Atlan 概念）
  - MNP の Surface 用 optional extension としての部分採用

## 関連ファイル

- `01_principles.md`
- `02_ssot_authority_map.md`
- `04_decision_rules.md`
- `../README.md`

## 最低 acceptance

- ミッション 1 文が明確
- 作る対象 8 種が列挙されている
- 作らない対象が列挙されている
- V3 との関係が継承 / 新規追加の 2 軸で書かれている

## 止める条件

- ミッションが「設計工場」以外の目的に拡張されようとしている
- V3 を破壊する方向に修正されている
- V4 が UI 本体 / 業務正本を所有する方向に拡張されている
