---
id: connect.topology_studio.v1
status: planned
owner: 11_connect
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 60_topology_studio.md — Topology Studio との接続

## 役割

V4 と Topology Studio（CompanyOS UI）の接続経路を定義します。接続は一方向であり、V4 は Topology Studio に表示データを投影（projection）しますが、Topology Studio からの直接書き戻しはありません。V4 は topology_exporter を通じて `.companyos/` interface への出力を行います。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`06_build/exporters/topology_exporter.md` の設計が固まり、Topology Studio との実際の接続が必要になった段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- V4 から Topology Studio への投影経路（projection contract）の定義
- topology_exporter が出力すべき形式と接続手段
- Topology Studio の Repo Card / Workflow Lens / Member Work Lens への対応方針
- freshness / source_pin の管理方針

## 持たないもの

- CompanyOS 全体との接続説明（→ `10_companyos_connection.md`）
- topology_exporter の実装仕様（→ `../06_build/exporters/topology_exporter.md`）
- Topology Studio 本体の実装（CompanyOS 側が所有）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- Topology Studio からの直接書き戻しを許可する記述が入った
- V4 の正本が Topology Studio の UI 設計に引きずられる記述が入った

## 関連ファイル

- `10_companyos_connection.md` — V4 と CompanyOS 全体の関係
- `../06_build/exporters/topology_exporter.md` — exporter 仕様（V4 正本）
