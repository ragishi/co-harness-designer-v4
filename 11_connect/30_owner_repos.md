---
id: connect.owner_repos.v1
status: planned
owner: 11_connect
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 30_owner_repos.md — owner repo 群との接続

## 役割

V4 と owner repo 群（note / youtube / sns など）の接続経路をまとめて定義します。接続は一方向であり、V4 は各 owner repo の業務正本に直接書き戻しません。複数の owner repo に共通する接続パターンを後段で整理する場所として住所を確保します。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。owner repo（note / youtube / sns）の archetype 設計が固まり、共通の接続パターンが見えてきた段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- note / youtube / sns の各 owner repo との接続方向・接続手段の定義
- 各 owner repo に共通する接続パターンの整理
- V4 が参照する各 owner repo の構造要素（SPOKE.yml / `.companyos/` interface）
- owner repo 群全体の freshness / source_pin 管理方針

## 持たないもの

- 接続方針の汎用ルール（→ `00_connection_policy.md`）
- 各 owner repo の業務正本（各 owner repo が所有）
- archetype 定義（→ `../04_archetypes/repo/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 接続が双方向化する（V4 から owner repo への書き戻しを許可する）記述が入った

## 関連ファイル

- `00_connection_policy.md` — 接続方針（一方向原則）
- `../04_archetypes/repo/` — owner repo 群の archetype 定義
