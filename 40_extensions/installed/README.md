---
id: extension.installed.v1
status: planned
owner: 40_extensions
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# installed/ — 採用済み extension 置き場

## 役割

`admission_criteria.md` の全条件を満たし、正式採用された **extension を置く場所**。
archetype が `depends_on` を宣言してよいのは、ここに置かれた extension のみ。
proposals からの昇格は admission_criteria を必ず通す。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本フォルダは MVP では空（.gitkeep のみ）。
`proposals/mnp_surface_pack/` は pilot 中であり installed ではない。
残り 6 extension は archetype 側で `depends_on` が宣言されたタイミングで「使いながら作る」。

## このフォルダが持つもの（後段）— 6 候補 extension

| extension | 想定 depends_on |
| --- | --- |
| `client_ops/` | client 系 archetype |
| `content_production/` | note / youtube / sns 系 archetype |
| `publish_pipeline/` | 公開処理を持つ owner 系 archetype |
| `analytics_ops/` | 公開後 KPI を必要とする archetype |
| `automation_pack/` | workflow_ops archetype |
| `custom_surface_pack/` | design_system archetype |

## このフォルダが持たないもの

- pilot 中の extension（→ `../proposals/`）
- archetype 定義本体（→ `../../04_archetypes/`）
- extension → archetype 方向の依存（一方向ルール違反）

## 最低 acceptance

- 本 stub の存在意義が読める
- 6 候補 extension の住所が確保されている
- `proposals/` との役割分担が明確

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- admission_criteria を skip して extension が昇格した
- extension が archetype を参照し始めた（一方向ルール違反）

## 関連ファイル

- `../00_extension_policy.md` — extension 基本方針
- `../admission_criteria.md` — 昇格条件
- `../proposals/` — pilot 中 extension
- `../../04_archetypes/` — archetype 定義
