---
id: reference.topology_studio_notes.v1
status: planned
owner: 10_references
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# topology_studio_notes.md — Topology Studio 深掘りノート

## 役割

Topology Studio（CompanyOS UI）に関する参考メモを置く場所です。出典管理は `source_pins.md` §4 に委譲しており、本 file は Topology Studio の UI 概念・表示 lens 設計の詳細な参考メモを後段で整理する場所として住所を確保します。**本 file は V4 の正本ではありません**。Topology Studio 本体は CompanyOS 側が所有します。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`11_connect/60_topology_studio.md` の設計検討が深まり、Topology Studio の参考資料が必要になった段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- Topology Studio の表示 lens（Repo Card / Workflow Lens / Member Work Lens）の参考メモ
- V4 から Topology Studio への投影経路（projection contract）の参考整理
- topology_exporter が出力すべき形式の参考メモ
- Topology Studio の今後の方向性に関する参考情報

## 持たないもの

- 出典表（取得日 / 公開状況）→ `source_pins.md` §4 を参照
- Topology Studio 本体の実装（CompanyOS 側が所有）
- V4 の接続仕様正本（→ `../11_connect/60_topology_studio.md`）
- exporter 仕様正本（→ `../06_build/exporters/topology_exporter.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- Topology Studio 本体の機密情報を本 file にコピーした
- 参考元を V4 正本として扱う記述が混入した

## 関連ファイル

- `source_pins.md` §4 — CompanyOS / Topology Studio の出典
- `../11_connect/60_topology_studio.md` — Topology Studio との接続（V4 正本）
- `../06_build/exporters/topology_exporter.md` — exporter 仕様（V4 正本）
