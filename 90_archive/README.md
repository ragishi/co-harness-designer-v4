# 90_archive/ — 退役

## 0. 30 秒で分かる役割

古くなったものを **消さずに保管** する場所。退役理由と代替先を残す。

V3 `90_archive/` の思想を継承（削除ではなく退役）。

## 1. このrootが持つもの

- archive policy（保管方針、後段）
- 退役した archetype / contract / scaffold / outputs
- 移行記録
- V3 への明示的 pointer (`99_legacy_v3_pointer.md`)

## 2. このrootが持たないもの

- 現役の正本
- 業務正本本体
- 削除されたファイルの内容（git history で十分なものは置かない）

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `00_archive_policy.md` | 保管方針 | — 後段 |
| `retired_archetypes/` | 退役 archetype | 空 |
| `retired_contracts/` | 退役 contract | 空 |
| `retired_scaffolds/` | 退役 scaffold | 空 |
| `retired_outputs/` | 退役完成物 | 空 |
| `migration_records/` | V3 → V4 等の移行記録 | 空 |
| `99_legacy_v3_pointer.md` | V3 への pointer | ✓ |

## 4. 読む順番

1. `README.md`
2. `99_legacy_v3_pointer.md`

## 5. 最低 acceptance

- 退役したものに「退役理由」「代替先」がある
- V3 への明示的 pointer がある
- archive policy（後段）が運用前に書かれる

## 6. 止める条件

- 退役理由のない archive がある
- 現役のものが archive に置かれた
- 業務正本本体が archive されている

## 7. 関連 root

- `../00_foundation/04_decision_rules.md`（migration）
- `../31_learning/`（rejected 候補の archive 経路）
