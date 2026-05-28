---
id: status_metric.artifact_status.v1
status: planned
owner: 03_status_metrics
note: "予定 enum は仮称（draft/published/archived/generated/stale 等）。active 化は 40_sync_status.md と同段階。"
---

# 30_artifact_status.md — artifact の共通 status

## 役割

V4 が産む target repo で扱う **Artifact**（成果物）の状態 enum を定義する。

Artifact の状態は workflow_status から派生するが、artifact 固有の生成・キャッシュ・公開サイクルを持つため、独立した enum として後段で定義する。

**planned stub であり後段で本格実装する。**

## MVP での扱い

本 file は MVP では active 化しない。

Artifact の状態追跡が必要になるのは、generated / surface の本格的な鮮度管理を実装する段階（`40_sync_status.md` と同期して active 化を検討）。

## 持つもの

- artifact status enum の定義（後段で確定）
- workflow_status との継承・差分関係
- UI 表示名
- CompanyOS 変換（→ `mapping_rules/` に委譲）

## 持つ予定の enum 概念（後段で確定）

後段で以下の概念を enum として整理する（確定前につき仮称）：

- `draft` — 作業中、まだ公開されていない artifact
- `published` — 公開済みの artifact
- `archived` — 退役済みの artifact
- `generated` — AI またはツールによって生成されたキャッシュ・投影物
- `stale` — 元ソースが更新済みだが再生成されていない状態（`40_sync_status.md` と重複検討）

実 enum 定義は本 file active 化時に `10_workflow_status.md` の命名規則と整合させる。

## 持たないもの

- workflow 自体の status（→ `10_workflow_status.md`）
- task の status（→ `20_task_status.md`）
- sync 鮮度（→ `40_sync_status.md`）
- 生成処理の実装コード

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- workflow_status と役割が混在する記述
- 生成処理の実装をここに書く

## 関連ファイル

- `10_workflow_status.md`（親 enum・命名規則の正本）
- `40_sync_status.md`（sync 状態との境界整理）
- `../01_meaning_model/10_entities.md`（Artifact entity 定義）
- `../06_build/scaffolds/companyos_interface/sync/freshness.md`
