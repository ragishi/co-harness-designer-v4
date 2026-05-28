# 06_build/ — 生成・変換（scaffold + exporter）

## 0. 30 秒で分かる役割

V4 が実際に **target repo を産み**、**CompanyOS UI 用の view を生成する** ための仕様置き場。

MVP では実装コード本体は持たず、**仕様（Markdown）と雛形（scaffold）** のみを置く。

## 1. このrootが持つもの

- build policy（生成・変換の基本方針）
- scaffolds/（target repo へコピーできる雛形）
- exporters/（CompanyOS UI 用 view 生成仕様）
- generated_policy（generated は正本にしないルール、後段）

## 2. このrootが持たないもの

- 実装コード本体（MVP 後段）
- target repo の業務正本
- contract の本文（→ `../02_contracts/`）

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `00_build_policy.md` | 生成・変換の基本方針 | — 後段 |
| `scaffolds/companyos_interface/` | `.companyos/` の雛形 | ✓ |
| `scaffolds/base_repo/` | target repo の最小雛形 | — 後段 |
| `scaffolds/{archetype}_repo/` | archetype 別雛形 | — 後段 |
| `exporters/mnp_surface_exporter.md` | MNP exporter 仕様（実装は後段） | ✓ |
| `exporters/{other}_exporter.md` | repo_card / workflow_lens / topology / surface | — 後段 |
| `generated_policy.md` | generated cache の扱い | — 後段 |

## 4. 読む順番

1. `README.md`
2. `scaffolds/companyos_interface/README.md`
3. `exporters/mnp_surface_exporter.md`

## 5. 最低 acceptance

- `scaffolds/companyos_interface/` に target repo へコピーできる雛形が揃う
- `exporters/mnp_surface_exporter.md` に exporter 仕様（実装でなく仕様）が書かれている
- すべての generated 物が source_pin を持つルールが明記されている

## 6. 止める条件

- scaffold に業務正本が入った
- exporter が業務正本を直接書き換える設計になっている
- generated 物が正本扱いされ始めた

## 7. 関連 root

- `../02_contracts/10_repo_contract.md`
- `../02_contracts/40_surface_contract.md`
- `../02_contracts/80_mnp_surface_contract.md`
- `../04_archetypes/`
- `../07_quality/30_critical_gates.md`
