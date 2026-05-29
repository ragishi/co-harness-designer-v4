---
id: build.exporter.topology.v1
status: planned
owner: 06_build
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# topology_exporter.md — Topology Studio 用 view 生成仕様

## 役割

複数の target repo の関係性・接続情報を入力として読み取り、CompanyOS UI の **Topology Studio** に表示可能な node/edge view を生成する exporter の **仕様**。

Topology Studio は target repo 群の接続トポロジーを俯瞰表示するための CompanyOS 機能である。この exporter は各 target repo の manifest と SPOKE.yml から接続関係を抽出して投影する。

**planned stub であり、後段で本格実装する（仕様であり実装コードではない）。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`11_connect/60_topology_studio.md` の Topology Studio 仕様が固まった後に本格実装する。

## 持つもの（後段で本格実装する内容）

- 入力仕様（各 target repo の manifest / SPOKE.yml から読み取る接続情報）
- 出力仕様（Topology Studio の node / edge view データ構造）
- 変換手順（repo 群 → topology view の step）
- source_pin の扱い（各 repo の出自を追跡）
- 止める条件（gate）

## 持たないもの

- 実装コード本体
- 業務正本そのもの
- Topology Studio の UI 仕様本文（→ `../../11_connect/60_topology_studio.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- exporter が業務正本を直接書き換える設計
- topology view が正本扱いされる設計

## 関連ファイル

- `../../11_connect/60_topology_studio.md` — Topology Studio 仕様（後段）
- `mnp_surface_exporter.md` — 参照すべき実体 exporter
- `../../02_contracts/40_surface_contract.md` — Surface Contract
