# 10_workflow_status.md — workflow の共通 status

## 役割

V4 が産む全 target repo の workflow / task で使う **共通 status enum** を定義する。

CompanyOS UI が読む正準形（`task_source_contract.yml` の status）と整合する。

## 持つもの

- 8 status の enum
- 各 status の意味
- 各 status の UI 表示名
- CompanyOS 側 enum との対応

## 持たないもの

- 計算実装
- archetype 固有 status（→ archetype 側で local status を持ち、mapping_rules で変換）

---

## 共通 workflow status

| status | 意味 | UI 表示 | CompanyOS 対応 |
| --- | --- | --- | --- |
| `planned` | まだ着手前 | 予定 | `todo` |
| `active` | 作業中 | 進行中 | `in_progress` |
| `review_needed` | 人間確認待ち | レビュー待ち | `review` |
| `blocked` | 止まっている | 停止中 | `blocked` |
| `publish_ready` | 公開準備完了 | 公開準備 OK | `review` |
| `published` | 公開済み | 公開済み | `done` |
| `learning` | 振り返り中 | 学習中 | `done` |
| `archived` | 退役済み | アーカイブ | `done` |

## 採用方針

- V4 内では 8 status enum を使う
- CompanyOS UI に渡すときは右列に従って 5 status enum (`todo / in_progress / blocked / review / done`) に変換する
- 変換は `mapping_rules/local_status_to_companyos.md`（MVP 後段）で実装

## 各 status の使用例

- `planned` — workflow が定義されたが、最初の Task が開始されていない
- `active` — 1 つ以上の Task が `in_progress`
- `review_needed` — Task が完了し、人間確認待ち
- `blocked` — 依存・承認・外部要因で前進不可
- `publish_ready` — 全 Task 完了、最終公開承認待ち
- `published` — 公開完了
- `learning` — 公開後の振り返り中
- `archived` — workflow 自体が退役

## 最低 acceptance

- 8 status の意味と UI 表示名が表で読める
- CompanyOS 側 enum との対応が書かれている

## 止める条件

- status enum が 8 を超えて増えた（DRR を通していない場合）
- CompanyOS の正準 5 status enum と矛盾した
- status の英語名が変更された（破壊的変更、必ず migration package を通す）

## 関連ファイル

- `../01_meaning_model/10_entities.md` §4 (Task) §2 (Workflow)
- `../02_contracts/40_surface_contract.md`
- `../02_contracts/20_workflow_contract.md`
- 後段：`mapping_rules/local_status_to_companyos.md`
