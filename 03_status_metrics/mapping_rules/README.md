---
id: status_metric.mapping_rules.v1
status: planned
owner: 03_status_metrics
note: "住所と役割確保のための stub。本格実装は後段。"
---

# mapping_rules/ — local status → CompanyOS 変換規則

## 役割

target repo の **local status**（V4 8 enum）を **CompanyOS UI 側の status enum**（5 enum）へ変換するルールを管理する subroot。

archetype 別の上書きルールも後段でここに追加する。

**planned stub であり後段で本格実装する。**

## MVP での扱い

本 subroot は MVP では active 化しない。`10_workflow_status.md` の採用方針セクションに変換対応表が掲載されており、それが現行の暫定正本。

本 subroot active 化のタイミング: CompanyOS integration の実 writeback / 投影を実装する段階。

## このフォルダが持つもの

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | — 後段 |
| `local_status_to_companyos.md` | V4 8 enum → CompanyOS 5 enum 変換表 | — 後段 |

後段では archetype 別上書きファイル（例: `note_archetype_overrides.md`）を追加する可能性がある。

## このフォルダが持たないもの

- status enum の定義本体（→ `../10_workflow_status.md`）
- CompanyOS 側 schema（→ `02_contracts/` および CompanyOS 正本）
- 変換処理の実装コード

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- status enum の定義をここに重複定義する
- 変換処理の実装コードをここに書く

## 関連ファイル

- `../10_workflow_status.md`（変換元 enum の正本）
- `local_status_to_companyos.md`（変換表の本体）
- `../../02_contracts/40_surface_contract.md`
