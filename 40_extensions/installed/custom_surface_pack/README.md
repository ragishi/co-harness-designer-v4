---
id: extension.installed.custom_surface_pack.v1
status: planned
owner: 40_extensions
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# custom_surface_pack/ — カスタム surface extension

## 役割

design_system archetype が `depends_on` する想定の、**カスタム UI surface 定義**を提供する extension。
`proposals/mnp_surface_pack/` が MNP 向けの Surface 部分採用 proposal であるのに対し、
本 extension は design_system archetype が必要とする汎用カスタム surface 定義を担う。
Markdown 正本から生成される surface であり、UI/HTML は canonical にならない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
design_system archetype が `depends_on: custom_surface_pack` を宣言し、admission_criteria を満たしたタイミングで本格実装する。

## このフォルダが持つもの（後段で本格実装する内容）

- カスタム surface スキーマ定義
- surface コンポーネント仕様（Markdown から生成）
- デザイントークン・カラー・タイポグラフィの定義テンプレート
- surface の再生成手順・source_pin 管理ルール

## このフォルダが持たないもの

- HTML/CSS/JS 本体（UI は projected view、canonical にならない）
- MNP 固有の surface（→ `../../proposals/mnp_surface_pack/`）
- archetype 定義（→ `../../../04_archetypes/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- surface が SSOT として扱われた（`../../../00_foundation/03_format_and_ui_policy.md` 違反）
- extension が archetype を参照し始めた（一方向ルール違反）

## 関連ファイル

- `../../proposals/mnp_surface_pack/` — MNP 向け surface proposal（別物）
- `../README.md` — installed 全体
- `../../../00_foundation/03_format_and_ui_policy.md` — UI は projected view
- `../../00_extension_policy.md` — 一方向依存ルール
