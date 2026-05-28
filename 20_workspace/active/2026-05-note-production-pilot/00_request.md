---
id: workspace.2026-05-note-production-pilot.00_request.v1
status: active
slug: 2026-05-note-production-pilot
owner: 04_archetypes
target_archetype: archetype.note_production_repo.v1
target_repo: co-note-production
---

# 00_request.md — 依頼内容

## 役割

この pilot 設計作業の **依頼そのもの** を、saku の意図に近い形で記録する。判断・整理は禁止（後段の 01-08 で行う）。

## 持つもの

- 元の依頼（意図翻訳）
- 成功条件 / 非成功条件
- 制約

## 持たないもの

- 詳細実装手順（→ `08_handoff.md`）
- 個別 surface の表示要素（→ `06_surface_design.md`）
- 品質判定の本体（→ `07_quality_plan.md`）

---

## 元の依頼（saku 意図の翻訳）

V4 が産む archetype `note_production_repo` を、最初の **projected target repo** として `co-note-production` に適用できるかを検証する。

具体的には：

- V4 の `06_build/scaffolds/companyos_interface/` を `co-note-production/.companyos/` にコピー適用
- `note_production_repo` archetype の制約（必須/禁止 module、表示/非表示要素）に従って surface / sync を埋める
- 業務正本（記事本文・draft・未公開メモ）が `.companyos/` 内に侵入しないことを確認
- target repo 側の既存 workflow を壊さない最小手数で動かす
- 結果を V4 の `30_feedback/raw/` に観測として残す

## 成功条件

「**Common Core 9 entries**（target repo の root 直下構造）」と「**`.companyos/` 内 10 file**（接続口 directory の中身）」は別の count。混同しない。

| # | 条件 | 判定方法 |
| --- | --- | --- |
| 1a | `co-note-production` の **Common Core 9 entries** が揃う（`.companyos/` を新規追加することで完成） | ls 確認 |
| 1b | `co-note-production/.companyos/` **内** の 10 file が揃う（README / manifest×2 / surfaces×3 / sync×3 / generated/README）| ls 確認 |
| 2 | 業務正本（記事本文・draft）が `.companyos/` 内に存在しない | grep + manifest 監査 |
| 3 | repo_card / workflow_lens / member_work_lens 3 surface が source_pin を持つ | `sync/source_pin.md` 監査 |
| 4 | `.companyos/generated/` 配下は README のみで実体 cache はゼロ | ls 確認 |
| 5 | V4 の Critical Gate（SSOT / UI not SSOT / Markdown-first / Source Pin / Contract / Common Core / MNP + V3 継承 3）を全て通る | /qg manual check |

## 非成功条件（= 失敗とみなす）

- 記事本文の copy が `.companyos/` 内にある
- generated/ に JSON 正本が書かれた
- MNP block が `.companyos/surfaces/` 外で使われている
- UI からの直接書き戻し path が新設された
- `co-note-production` 既存 root の追加 / 名称変更が起きた

## 制約

- V4 (`co-harness-designer-v4`) の root 構造は変更しない
- V3 (`co-harness-design-v3`) は触らない
- 本 pilot 作業は **Phase 2: V4 内の設計パッケージ作成のみ**
- `co-note-production` 側への実装は Phase 3（別 task / 別 session）で実施する

## 関連ファイル

- 親 read_set: `../../../05_read_sets/companyos_repo_design_read_set.md`
- 採用 archetype 本体: `../../../04_archetypes/repo/note_production_repo.md`
- target repo: `co-note-production`（V4 外、Phase 3 で適用）
- 観測記録先: `../../../30_feedback/raw/2026-05.md`
