# 31_learning/ — 抽象化された学び

## 0. 30 秒で分かる役割

`30_feedback/raw/` の生の観測を **再利用できる学び** に変換する場所。

V3 の signal registry / 4-AND 昇格門の思想を継承。**ここが「使うほど改善されていく OS」の心臓**。

## 1. このrootが持つもの

- 昇格 protocol（00_promotion_protocol）
- signals/ — 繰り返し出る兆候
- patterns/ — 抽象化されたパターン
- candidates/ — 正式採用候補
- accepted/ — 採用済み
- rejected/ — 却下済み
- promotion_queue.md — 昇格待ち（後段）

## 2. このrootが持たないもの

- raw 観測（→ `../30_feedback/raw/`）
- 業務正本
- 削除された entry の内容（rejected で扱う）

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `_index.md` | 昇格 navigate | — 後段 |
| `00_promotion_protocol.md` | 昇格手続き | ✓ |
| `signals/` | 兆候（追跡対象） | ✓ 空 |
| `patterns/` | 抽象化パターン | — 後段 |
| `candidates/` | 採用候補 | — 後段 |
| `accepted/` | 採用済み | — 後段 |
| `rejected/` | 却下済み | — 後段 |
| `promotion_queue.md` | 昇格待ちキュー | — 後段 |

## 4. 読む順番

1. `README.md`
2. `00_promotion_protocol.md`

## 5. 最低 acceptance

- 昇格 protocol が明文化されている
- 4-AND 昇格門（再発 ≥ 3 / 冷却 ≥ 7 日 / grader pass / boundary check pass）が継承されている
- signals → patterns → candidates → accepted / rejected の流れが説明されている

## 6. 止める条件

- 昇格 protocol を skip して accepted に直接書き込んだ
- raw が `31_learning/` に直接置かれた
- accepted が `00`-`07` の正式設計に反映されないまま放置された

## 7. 関連 root

- `../30_feedback/` — raw の供給元
- `../00_foundation/`-`../07_quality/` — accepted の反映先
