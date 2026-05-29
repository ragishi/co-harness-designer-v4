---
id: status_metric.status_map.v1
status: planned
owner: 03_status_metrics
note: "住所と役割確保のための stub。本格実装は後段。"
---

# 00_status_map.md — 状態全体地図

## 役割

`03_status_metrics/` 配下の全 file を index し、各 file の役割・MVP 状況・読む順番を一覧で示す。

他 AI が「どの status file が存在するか / active か / planned か」を迷わず判断できるようにすることが目的。

**planned stub であり後段で本格実装する。** MVP では `10_workflow_status.md` のみが active。

## MVP での扱い

本 file は MVP では active 化しない。`README.md` §3 File Map が暫定 index として代用している。

後段で `03_status_metrics/` への file 追加が増えた時点で本 file を実装し、README の File Map と差分なく同期する。

## 持つもの

- `03_status_metrics/` 全 file の path・役割・MVP status の index 表
- active / planned 区別の凡例
- 各 file を読む推奨順序

## 持たないもの

- 各 file の status enum 定義（→ 各 file 本体）
- entity 意味（→ `../01_meaning_model/`）
- 計算実装

---

## File Index（後段で詳細化）

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | root 入口・全体概要 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `00_status_map.md` | この全体地図 | — 後段 |
| `10_workflow_status.md` | workflow / task 共通 status enum（8 enum） | ✓ |
| `20_task_status.md` | task status（MVP: workflow_status 流用） | — 後段 |
| `30_artifact_status.md` | artifact の status enum | — 後段 |
| `40_sync_status.md` | sync 鮮度状態 | — 後段 |
| `50_quality_scores.md` | 品質スコア概念 | — 後段 |
| `60_readiness_scores.md` | 公開・実行準備スコア概念 | — 後段 |
| `mapping_rules/README.md` | mapping_rules subroot 入口 | — 後段 |
| `mapping_rules/local_status_to_companyos.md` | local → CompanyOS enum 変換 | — 後段 |
| `mapping_rules/workflow_to_lens.md` | workflow status → CompanyOS Lens 変換 | — 後段 |
| `mapping_rules/artifact_to_surface.md` | artifact status → Surface 表示変換 | — 後段 |

凡例: ✓ = MVP active / — 後段 = planned stub（住所と役割確保済み）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 他 file の enum 定義をここに重複定義する
- active でないのに「完成」と誤読される記述

## 関連ファイル

- `README.md`（File Map の現行版）
- `10_workflow_status.md`（唯一の active status file）
- 各 planned stub（20〜60 + mapping_rules/）
