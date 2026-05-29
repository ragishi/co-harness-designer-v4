---
id: connect.prompt_repo.v1
status: planned
owner: 11_connect
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 40_prompt_repo.md — prompt repo との接続

## 役割

V4 と prompt repo の接続経路を定義します。接続は一方向であり、V4 は prompt repo の業務正本に直接書き戻しません。重要な制約として、**prompt は SSOT を内包しません**。prompt repo は prompt テキストを管理する場所であり、V4 の設計正本・archetype・契約を所有しません。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。prompt repo の archetype 設計が固まり、実際の接続が必要になった段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- prompt repo との接続方向・接続手段の定義
- V4 が参照する prompt repo の構造要素（SPOKE.yml / `.companyos/` interface）
- prompt repo に求める最低要件
- 「prompt は SSOT を内包しない」制約の具体的な境界説明

## 持たないもの

- 接続方針の汎用ルール（→ `00_connection_policy.md`）
- prompt repo の業務正本（prompt repo が所有）
- archetype 定義（→ `../04_archetypes/repo/prompt_repo.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- prompt を V4 の SSOT として扱う記述が入った
- 接続が双方向化する記述が入った

## 関連ファイル

- `00_connection_policy.md` — 接続方針（一方向原則）
- `../04_archetypes/repo/prompt_repo.md` — prompt repo の archetype 定義
