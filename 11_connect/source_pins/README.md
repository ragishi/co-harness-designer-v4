---
id: connect.source_pins.v1
status: planned
owner: 11_connect
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# source_pins/ — 接続契約への参照集

## 役割

V4 の各接続先（CompanyOS / target repo 群 / Topology Studio / Atlas）との接続契約・SPOKE.yml への source_pin を置く場所です。接続の実体説明は各 `NN_*.md` が持ち、本フォルダはそれらへの参照 pin を整理します。

> 区別: `../../10_references/source_pins.md` は**外部参考元（Atlan / MNP / V3 / CompanyOS 資料）の出典 pin**。こちら（`11_connect/source_pins/`）は**接続契約・SPOKE.yml への参照 pin**。用途が異なります。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本フォルダは MVP ではまだ使わない（active 化しない）。各接続先の SPOKE.yml・契約が確定した段階で本格実装する。

## このフォルダが持つもの

| path（後段で追加） | 役割 |
| --- | --- |
| `companyos.md`（後段）| CompanyOS 接続契約への source_pin |
| `project_progress_repo.md`（後段）| project_progress repo の SPOKE.yml への source_pin |
| `owner_repos.md`（後段）| owner repo 群の SPOKE.yml への source_pin |
| `prompt_repo.md`（後段）| prompt repo の SPOKE.yml への source_pin |
| `design_system_repo.md`（後段）| design system repo の SPOKE.yml への source_pin |
| `topology_studio.md`（後段）| Topology Studio 接続契約への source_pin |
| `atlas.md`（後段）| Atlas 接続契約への source_pin |

## このフォルダが持たないもの

- 接続の実体説明（→ 各 `../NN_*.md`）
- 外部参考元の出典 pin（→ `../../10_references/source_pins.md`）
- V4 正本（→ `../../00_foundation/` 〜 `../../07_quality/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- `10_references/source_pins.md` との役割の違いが明確に読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 外部参考元の出典（Atlan / MNP / V3 等）を本フォルダに置いた（`10_references/source_pins.md` が正しい置き場）
- 接続説明本体を本フォルダに置いた（各 `NN_*.md` が正しい置き場）

## 関連ファイル

- `../00_connection_policy.md` — 接続方針（一方向原則）
- `../../10_references/source_pins.md` — 外部参考元の出典 pin（別用途）
