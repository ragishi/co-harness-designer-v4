---
id: status_metric.sync_status.v1
status: planned
owner: 03_status_metrics
note: "住所と役割確保のための stub。本格実装は後段。予定語彙のみ列挙。自動同期処理・実装コードなし。"
---

# 40_sync_status.md — sync 鮮度状態

## 役割

target repo の generated 物・surface が source_pin に対してどれだけ最新か（鮮度）を表す **sync 状態語彙** を定義する。

CompanyOS UI 側で「この情報は古い可能性があります」と判定するための根拠となる。

**planned stub であり後段で本格実装する。** 自動同期処理・実装コードは書かない。

## MVP での扱い

本 file は MVP では active 化しない。

sync 鮮度管理が必要になるのは、`06_build/scaffolds/companyos_interface/sync/freshness.md` の scaffold を target repo に展開し始める段階。

## 持つもの

- sync 状態語彙（予定 4 語）の定義
- 各語彙の判定条件の概念説明
- `freshness.md` の stale 判定との整合指針

## 持たないもの

- 自動同期処理・実装コード
- CompanyOS API 連携
- artifact の内容 status（→ `30_artifact_status.md`）
- 生成 cadence 設定（→ `freshness.md` scaffold）

---

## 予定語彙（後段で enum として確定）

以下は予定語彙のみ。**実 enum 定義・実装コードは本 file active 化時に行う。**

| 語彙 | 意味 |
| --- | --- |
| `fresh` | source_pin から最近再生成されており、UI に表示しても安全な状態。freshness.md で定義した cadence 内に収まっている。 |
| `stale` | source 側 file が更新済みだが、generated / surface がまだ再生成されていない状態。UI 側で警告を表示する。 |
| `missing_source` | source_pin が指すファイルが解決できない、または存在しない状態。再生成が不可能であることを示す。 |
| `blocked` | 同期処理を進めることができない状態（権限不足・外部依存 / downstream 未応答など）。`10_workflow_status.md` の `blocked` と対応。 |

これらは `freshness.md` の `stale` 判定と整合させる。確定時に本 file と freshness.md の用語が矛盾しないよう確認する。

## 最低 acceptance

- 本 stub の存在意義が読める
- 予定 4 語彙とその意味が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 自動同期処理・API 連携コードをここに書く
- artifact の内容 status と混在する記述

## 関連ファイル

- `10_workflow_status.md`（`blocked` との整合）
- `30_artifact_status.md`（artifact 状態との境界）
- `../06_build/scaffolds/companyos_interface/sync/freshness.md`（stale 判定の scaffold 正本）
- `mapping_rules/local_status_to_companyos.md`（CompanyOS 変換）
