---
id: status_metric.mapping_rules.local_to_companyos.v1
status: planned
owner: 03_status_metrics
note: "住所と役割確保のための stub。本格実装は後段。変換表は 10_workflow_status.md の正本と一致。"
---

# local_status_to_companyos.md — local status → CompanyOS 変換

## 役割

V4 の **local 8 enum** を **CompanyOS UI 側の 5 enum** へ変換する正本ルールを定義する。

`10_workflow_status.md` の採用方針に記載の対応表を、この file が後段で正本として引き受ける。

**planned stub であり後段で本格実装する。** 現時点の正本は `../10_workflow_status.md` §採用方針。

## MVP での扱い

本 file は MVP では active 化しない。`../10_workflow_status.md` の採用方針セクションが変換対応表の暫定正本として機能している。

本 file active 化と同時に `10_workflow_status.md` の変換表をここへ移管し、`10_workflow_status.md` からはここへのポインターに差し替える。

---

## 変換表（`10_workflow_status.md` 正本と一致）

| V4 local status | CompanyOS status | 変換根拠 |
| --- | --- | --- |
| `planned` | `todo` | 着手前。CompanyOS で「やること」として表示 |
| `active` | `in_progress` | 作業中。CompanyOS で「進行中」として表示 |
| `review_needed` | `review` | 人間確認待ち。CompanyOS の review state に直接対応 |
| `blocked` | `blocked` | 停止中。CompanyOS の blocked state に直接対応 |
| `publish_ready` | `review` | 公開前の最終確認中。CompanyOS では review として扱う（publish_ready は V4 固有の細分） |
| `published` | `done` | 公開完了。CompanyOS では done として扱う |
| `learning` | `done` | 振り返り中。公開後のフェーズであり CompanyOS では done 扱い |
| `archived` | `done` | 退役済み。CompanyOS では done として表示 |

## 後段で追加する内容

- archetype 別上書きルール（例: note archetype では `learning` を `in_progress` として扱う場合など）
- 変換の優先順位（local が複数 status を持つ場合のマージルール）
- CompanyOS API への serialization 形式

## 最低 acceptance

- 本 stub の存在意義が読める
- V4 8 enum → CompanyOS 5 enum の変換表が `10_workflow_status.md` と一致している
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- `10_workflow_status.md` の変換表と矛盾する定義をここに書く
- archetype 固有ルールを汎用ルールとして上書きする

## 関連ファイル

- `README.md`（この subroot 入口）
- `../10_workflow_status.md`（変換元 enum・現行正本）
- `../../02_contracts/40_surface_contract.md`
- `../../02_contracts/60_writeback_contract.md`
