---
id: connect.project_progress_repo.v1
status: planned
owner: 11_connect
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 20_project_progress_repo.md — project_progress repo との接続

## 役割

V4 と project_progress repo の接続経路を定義します。接続は一方向であり、V4 は project_progress repo の業務正本に直接書き戻しません。project_progress repo の archetype に基づいて接続仕様を後段で整理する場所として住所を確保します。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。project_progress repo の archetype 設計が固まり、実際の接続が必要になった段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- project_progress repo との接続方向・接続手段の定義
- V4 が参照する project_progress repo の構造要素（SPOKE.yml / `.companyos/` interface）
- 接続時の freshness / source_pin 管理方針
- project_progress repo 側に求める最低要件

## 持たないもの

- 接続方針の汎用ルール（→ `00_connection_policy.md`）
- project_progress repo の業務正本（project_progress repo が所有）
- archetype 定義（→ `../04_archetypes/repo/project_progress_repo.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 接続が双方向化する（V4 から project_progress repo への書き戻しを許可する）記述が入った

## 関連ファイル

- `00_connection_policy.md` — 接続方針（一方向原則）
- `../04_archetypes/repo/project_progress_repo.md` — archetype 定義
