---
id: workspace.2026-05-note-production-pilot.01_scope.v1
status: active
slug: 2026-05-note-production-pilot
---

# 01_scope.md — 対象範囲

## 役割

`00_request.md` の依頼を **in scope / out of scope** に固定する。

## 持つもの

- in scope（V4 内 + Phase 3 で target に作るものの設計範囲）
- out of scope（やらない）
- 対象 archetype / contract / metric

## 持たないもの

- 実装手順（→ `08_handoff.md`）
- ssot 割り当ての詳細（→ `03_ssot_map.md`）

---

## In scope

### Phase 2（本パッケージ）— V4 内

- `20_workspace/active/2026-05-note-production-pilot/` の 9 設計ファイル（本パッケージ）
- `30_feedback/raw/2026-05.md` への pilot 開始記録（既に append 済）

### Phase 3 で `co-note-production` 側に作るものの **設計**（実装は本パッケージ外）

- `.companyos/README.md`（接続口宣言）
- `.companyos/manifest.md`（Markdown 正本）
- `.companyos/manifest.yml`（最小限の機械読み版）
- `.companyos/surfaces/repo_card.surface.md`
- `.companyos/surfaces/workflow_lens.surface.md`
- `.companyos/surfaces/member_work_lens.surface.md`
- `.companyos/sync/source_pin.md`
- `.companyos/sync/freshness.md`
- `.companyos/sync/generated_from.md`
- `.companyos/generated/README.md`

→ 合計 10 file（`.companyos/manifest.md` + `manifest.yml` で 2、surfaces 3、sync 3、generated 1、README 1）。

## Out of scope（やらない）

| 項目 | 理由 |
| --- | --- |
| 記事本文の `.companyos/` 移動 / コピー | 業務正本は通常 directory に置く（`contract.surface.v1` 違反） |
| `generated/` 配下の実 cache 作成 | MVP は仕様のみ、実 build pipeline は後段 |
| MNP parser / serializer の実装 | proposals/ pilot 段階、installed/ 昇格前 |
| JSON 生成パイプライン | Markdown-first 検証が先 |
| 自動 exporter 実装（HTML / lens JSON） | 手動 surface で十分 |
| writeback path の実装 | `contract.writeback.v1` は planned stub のまま |
| `co-note-production` の既存 root 構造変更 | archetype 適用は Common Core 9 entries の有無確認のみ |
| `co-note-production` の既存 workflow / archetype 固有 root の編集 | 本 pilot は `.companyos/` 追加のみ |
| `note_production_read_set.md` の追加 | 本 pilot 完了 → feedback 観察 → 必要なら後段で追加 |

## 対象 archetype

- 採用: `archetype.note_production_repo.v1`
- 必須 module: `content_production`, `publish_pipeline`, `feedback_loop`（built-in）
- 推奨 module: `analytics_ops`
- 禁止 module: `client_ops`（archetype mismatch）

## 対象 contract（active）

- `contract.repo.v1`（Common Core 9 entries 遵守）
- `contract.workflow.v1`（target 内 workflow の書き方）
- `contract.surface.v1`（UI 連携の中核）
- `contract.markdown.v1`（Markdown 正本構造）
- `contract.mnp_surface.v1`（MNP block 使用条件）
- `contract.writeback.v1`（planned stub、参照のみ）

## 対象 metric

- `semantic.workflow_status.v1`（V4 内 8 enum、CompanyOS 側 5 enum へ変換）

## 関連ファイル

- `00_request.md`
- `02_archetype_choice.md`（archetype 採用根拠）
- `../../../04_archetypes/repo/note_production_repo.md`
- `../../../02_contracts/00_contract_map.md`
