---
id: connect.atlas.v1
status: planned
owner: 11_connect
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 70_atlas.md — Atlas 接続地図

## 役割

V4 と Atlas の接続経路を定義します。接続は一方向であり、V4 は Atlas への参照・投影を行いますが、Atlas からの直接書き戻しはありません。Atlas が何を指すか（CompanyOS 内の地図機能か、別サービスか）は後段の設計確認時に確定します。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。Atlas の役割・接続方式が確定した段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- Atlas の役割定義（V4 との関係での位置づけ）
- V4 から Atlas への接続方向・接続手段の定義
- Atlas が扱うデータ種別と V4 の対応要素の整理
- freshness / source_pin の管理方針

## 持たないもの

- 接続方針の汎用ルール（→ `00_connection_policy.md`）
- Atlas 本体の実装（Atlas 側が所有）
- V4 の正本（→ `../00_foundation/` 〜 `../07_quality/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- Atlas の役割が未確定のまま V4 正本に混入した
- 接続が双方向化する記述が入った

## 関連ファイル

- `00_connection_policy.md` — 接続方針（一方向原則）
