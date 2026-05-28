---
id: workspace.2026-05-note-production-pilot.07_quality_plan.v1
status: active
slug: 2026-05-note-production-pilot
---

# 07_quality_plan.md — 品質ゲート

## 役割

本 pilot が Phase 3 で `co-note-production` に適用されたあと、**何をもって合格とするか**を確定する。

## 持つもの

- 適用する Common Quality（9 項目）
- archetype 別の追加品質（note 固有）
- Critical Gate / Stop Conditions の運用
- acceptance criteria（成功 / 失敗判定）

## 持たないもの

- gate 本体の定義（→ `../../../07_quality/`）
- 計算実装

---

## 適用する Common Quality（9 項目、Phase 3 で全て満たす）

| # | 項目 | 本 pilot での判定 |
| --- | --- | --- |
| 1 | SSOT | 記事本文 / meta が `.companyos/` 内に重複していない |
| 2 | Markdown-first | `.companyos/manifest.md` が Markdown 正本、yml は機械読み |
| 3 | UI not SSOT | `.companyos/README.md` に「接続口であり正本ではない」明記 |
| 4 | Source Pin | 3 surface 全要素が `sync/source_pin.md` に登録 |
| 5 | Feedback Loop | Phase 3 完了後に `30_feedback/raw/2026-05.md` に観測 append |
| 6 | Drift Check | `.companyos/` 内に新規 root を追加していない（10 file 限定） |
| 7 | Permission Boundary | UI → 業務正本 直接書き戻しがない（writeback contract stub のまま） |
| 8 | Generated not Canonical | `.companyos/generated/` 配下は README のみ、cache 実体ゼロ |
| 9 | MNP not SSOT | MNP block を本 pilot では書かない（installed/ 昇格前） |

参照: `../../../07_quality/10_common_quality.md`

## archetype 別追加品質（note_production_repo 固有、本 pilot で確認）

| 項目 | 判定 |
| --- | --- |
| **記事本文の境界** | `draft.md` / `meta.md` が `20_workspace/articles/{slug}/` に閉じている |
| **公開準備状態** | `publish_ready` status が `meta.md` で正確に管理されている |
| **必須 module 宣言** | `SPOKE.yml` に `content_production`, `publish_pipeline` が宣言されている |
| **禁止 module の不在** | `client_ops` module が installed されていない |
| **workflow 整合** | `02_workflows/note_article_production.md` が `contract.workflow.v1` を満たす（本 pilot では確認のみ） |

参照: `../../../04_archetypes/repo/note_production_repo.md`

## Critical Gates（Phase 3 で全て pass、1 つでも失敗で止める）

| Gate | 止める条件（本 pilot 文脈） |
| --- | --- |
| **SSOT Gate** | `.companyos/` 内に記事本文 / draft の copy が存在 |
| **UI not SSOT Gate** | `.companyos/manifest.md` が業務正本を主張、または HTML に業務正本が直書き |
| **Markdown-first Gate** | manifest.yml だけ存在、manifest.md がない |
| **Source Pin Gate** | 3 surface のいずれかが source_pin を欠く |
| **Contract Gate** | `contract.repo.v1` 必須要素（Common Core 9 entries）が欠ける |
| **Common Core Gate** | Common Core 9 entries が揃っていない |
| **`.companyos/` not Canonical Gate** | `.companyos/` 内に業務正本がコピー |
| **Generated not Canonical Gate** | `.companyos/generated/` 配下が手動編集されている |
| **DRR Gate** | `.companyos/` 内に未承認の新 sub-dir 追加 |
| **MVP Boundaries Gate** | scope 外（MNP 実装 / writeback / JSON 生成）に手を出した |

### MNP 関連 Critical Gates（本 pilot では「MNP を書かない」で全て pass）

| Gate | 本 pilot での扱い |
| --- | --- |
| MNP Not SSOT | MNP block を書かないので自動 pass |
| MNP Source Pin | 同上 |
| MNP Parse | 同上 |
| MNP Contract | 同上 |
| MNP Writeback | 同上 |
| MNP Location | 同上 |

### V3 継承 Critical Gates（本 pilot で必ず pass）

`../../../07_quality/30_critical_gates.md` の "V3 継承の Critical Gate" 群。Common / MNP と同じく AND で運用（1 つでも失敗で止める）。

| Gate | 本 pilot での止める条件 |
| --- | --- |
| **Permission Boundary Gate** | UI からの直接書き戻しが許可されている（`contract.writeback.v1` planned stub の intent → 人間承認 → 正本更新 経路を skip） |
| **Feedback Loop Gate** | Phase 3 完了時に `co-note-production/30_feedback/raw/{YYYY-MM}.md` と V4 `30_feedback/raw/2026-05.md` の両方に observation entry が追加されていない |
| **V3 not Modified Gate** | `co-harness-design-v3` リポジトリを書き換えようとした |

参照: `../../../07_quality/30_critical_gates.md` + `../../../CLAUDE.gate.md`

## Stop Conditions（人間 review を求める）

- 既存 root を追加・名称変更しようとした
- 業務正本を `.companyos/` に置こうとした
- writeback path を新設しようとした
- MNP block を `.companyos/surfaces/` 外に置こうとした
- V3 (`co-harness-design-v3`) を編集しようとした
- V4 (`co-harness-designer-v4`) の root 構造を変更しようとした

## acceptance criteria（本 pilot Phase 3 完了の合格基準）

### 必須（10 中 10 を満たす）

1. `co-note-production/.companyos/` に 10 file が揃う
2. 業務正本（記事本文 / draft）が `.companyos/` 内に存在しない（grep で 0 件）
3. 3 surface 全てが source_pin を持つ
4. `.companyos/generated/` 配下は README のみ
5. 全 Critical Gates（共通 + MNP）が pass
6. Common Core 9 entries が揃う
7. `SPOKE.yml` に archetype 宣言と必須 module 宣言がある
8. `.companyos/manifest.md` と `manifest.yml` が整合している
9. V3 / V4 の root 構造に変更がない
10. `30_feedback/raw/2026-05.md` に Phase 3 完了の observation entry が追加されている

### 警告（advisory、推奨）

- 各 surface の表示要素数が「画面で読みやすい」適度な量
- README の文体が target repo の既存 README と整合
- manifest.md / surface .md の section 構造が `contract.markdown.v1` の標準テンプレに沿う

## 関連ファイル

- `06_surface_design.md`
- `08_handoff.md`（acceptance を実装者に渡す）
- `../../../07_quality/10_common_quality.md`
- `../../../07_quality/30_critical_gates.md`
- `../../../CLAUDE.gate.md`
