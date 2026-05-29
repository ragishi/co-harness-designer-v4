---
id: extension.proposals.v1
status: planned
owner: 40_extensions
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# proposals/ — pilot 中 extension 置き場

## 役割

`admission_criteria.md` の全条件を満たす前の **pilot 中 extension** を置く場所。
archetype が `depends_on` を宣言してもよいが、experimental 扱い。
`installed/` への昇格は admission_criteria を全条件クリアしてから。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本フォルダには `mnp_surface_pack/`（実体あり）が存在する。
他の extension はまだ proposals にも入っていない（`installed/` のスタブのみ）。

## このフォルダが持つもの（File Map）

| path | 役割 | MVP |
| --- | --- | :---: |
| `mnp_surface_pack/` | MNP の Surface 用 pilot extension（実体あり） | ✓ |

## このフォルダが持たないもの

- 採用済み extension（→ `../installed/`）
- archetype 定義（→ `../../04_archetypes/`）
- admission を skip した昇格候補

## 最低 acceptance

- 本 stub の存在意義が読める
- `mnp_surface_pack/` が唯一の pilot 中 extension であることが明確
- `installed/` との役割分担が分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- proposal が admission_criteria を skip して installed に昇格した
- `installed/` との境界が曖昧になった

## 関連ファイル

- `../00_extension_policy.md` — extension 基本方針
- `../admission_criteria.md` — 昇格条件
- `../installed/README.md` — 採用済み extension
- `mnp_surface_pack/README.md` — MNP Surface pilot
