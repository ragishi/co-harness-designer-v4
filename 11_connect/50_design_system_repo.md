---
id: connect.design_system_repo.v1
status: planned
owner: 11_connect
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 50_design_system_repo.md — design system repo との接続

## 役割

V4 と design system repo の接続経路を定義します。接続は一方向であり、V4 は design system repo の業務正本に直接書き戻しません。design system repo は UI コンポーネント・デザイントークンを管理する場所であり、V4 の設計正本を所有しません。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。design system repo の archetype 設計が固まり、実際の接続が必要になった段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- design system repo との接続方向・接続手段の定義
- V4 が参照する design system repo の構造要素（SPOKE.yml / `.companyos/` interface）
- design system repo に求める最低要件
- V4 scaffold が design system repo のトークンをどう参照するかの整理

## 持たないもの

- 接続方針の汎用ルール（→ `00_connection_policy.md`）
- design system repo の業務正本（design system repo が所有）
- archetype 定義（→ `../04_archetypes/repo/design_system_repo.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 接続が双方向化する（V4 から design system repo への書き戻しを許可する）記述が入った

## 関連ファイル

- `00_connection_policy.md` — 接続方針（一方向原則）
- `../04_archetypes/repo/design_system_repo.md` — design system repo の archetype 定義
