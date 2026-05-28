# 03_status_metrics/ — 状態・指標

## 0. 30 秒で分かる役割

Atlan でいう **セマンティックレイヤー相当**。CompanyOS や target repo で使う **状態・指標** を統一する。

V4 で扱うのは売上や LTV ではなく、**workflow status / task status / quality / readiness / sync state**。

## 1. このrootが持つもの

- 状態全体地図（status_map）
- workflow / task / artifact / sync の共通 status enum
- quality / readiness の score 定義
- mapping rules（target repo local status → CompanyOS status）

## 2. このrootが持たないもの

- entity 意味（→ `../01_meaning_model/`）
- 約束（→ `../02_contracts/`）
- 計算実装

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `00_status_map.md` | 状態全体地図 | — 後段 |
| `10_workflow_status.md` | workflow の共通 status | ✓ |
| `20_task_status.md` | task の共通 status | — 後段 |
| `30_artifact_status.md` | artifact の共通 status | — 後段 |
| `40_sync_status.md` | sync 状態 | — 後段 |
| `50_quality_scores.md` | 品質スコア | — 後段 |
| `60_readiness_scores.md` | 公開準備 score | — 後段 |
| `mapping_rules/` | local → CompanyOS マッピング | — 後段 |

MVP では `10_workflow_status.md` のみ。残りは使いながら追加。

## 4. 読む順番

1. `README.md`
2. `10_workflow_status.md`

## 5. 最低 acceptance

- workflow の共通 status enum が定義されている
- enum は CompanyOS 側 `task_source_contract.yml` の status と整合
- 各 status に UI 表示名がある

## 6. 止める条件

- status enum が CompanyOS と矛盾し始めた
- archetype 固有 status をここに混ぜている
- score の計算実装をここに書き始めた

## 7. 関連 root

- `../01_meaning_model/10_entities.md`
- `../02_contracts/40_surface_contract.md`
- `../07_quality/`
