# 20_workspace/ — 作業中

## 0. 30 秒で分かる役割

V4 で実際の **設計作業** を行う場所。完成物は `../21_outputs/` に移される。

V3 `20_workspace/` を継承。

## 1. このrootが持つもの

- active/ — 進行中の設計作業（slug 単位）
  - `_template/` — 雛形（コピーして使う）
- inbox/ — 受け取った依頼の初期受信
- experiments/ — 試行錯誤
- runs/ — 実行ログ / 1 回限りの作業

## 2. このrootが持たないもの

- 完成物（→ `../21_outputs/`）
- 生 feedback（→ `../30_feedback/`）
- 業務正本

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `active/README.md` | active の使い方 | ✓ |
| `active/_template/` | 設計作業の 9 step 雛形 | ✓ |
| `active/{YYYY-MM-{slug}}/` | 実 slug（コピーして作る） | 空 |
| `inbox/` | 受信箱 | 空 |
| `experiments/` | 実験 | 空 |
| `runs/` | 実行ログ | 空 |

## 4. 読む順番

1. `README.md`
2. `active/README.md`
3. `active/_template/00_request.md`

## 5. 最低 acceptance

- `active/_template/` に 9 step すべて存在
- 各 step に「役割 / 持つもの / 持たないもの」がある
- 実 slug が `_template/` をコピーする慣習が明文化されている

## 6. 止める条件

- `_template/` が直接編集された（毎回コピーして使う）
- active 配下に業務正本本体が置かれた
- 完成物が active 配下に放置された（21_outputs/ に移すべき）

## 7. 関連 root

- `../05_read_sets/companyos_repo_design_read_set.md` — 設計時に読むセット
- `../21_outputs/`
- `../30_feedback/`
