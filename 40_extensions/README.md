# 40_extensions/ — 後付け拡張

## 0. 30 秒で分かる役割

最初から core に入れない **追加機能 pack** を置く場所。

V3 `40_extension/` の admission gate 思想を継承。archetype が depends_on する機能 pack をここで管理する。

## 1. このrootが持つもの

- 拡張方針（extension_policy）
- 採用基準（admission_criteria）
- `installed/` — 採用済み extension（MVP では空）
- `proposals/` — pilot 中 extension
  - `mnp_surface_pack/` — MNP の Surface 用部分採用 proposal

## 2. このrootが持たないもの

- core 機能（→ `../00_foundation/`-`../07_quality/`）
- archetype 定義（→ `../04_archetypes/`）
- 業務正本

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `00_extension_policy.md` | 拡張方針 | ✓ |
| `admission_criteria.md` | 採用基準 | ✓ |
| `installed/` | 採用済み（MVP では空） | 空 |
| `proposals/mnp_surface_pack/` | MNP の Surface 用 pilot | ✓ |

## 4. 読む順番

1. `README.md`
2. `00_extension_policy.md`
3. `admission_criteria.md`
4. `proposals/mnp_surface_pack/README.md`

## 5. 最低 acceptance

- extension_policy と admission_criteria が明文化されている
- `installed/` と `proposals/` の役割分担が明確
- MNP は `proposals/` に居て `installed/` には**いない**

## 6. 止める条件

- proposal が admission_criteria を skip して installed に昇格した
- core 機能が extension として後付けされた
- extension が業務正本を持ち始めた

## 7. 関連 root

- `../04_archetypes/00_archetype_framework.md`（archetype と extension の一方向関係）
- `../00_foundation/04_decision_rules.md`（DRR + L0-L4）
- `../31_learning/00_promotion_protocol.md`（昇格 protocol）
