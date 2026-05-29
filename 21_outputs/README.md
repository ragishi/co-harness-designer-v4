# 21_outputs/ — 完成物

## 0. 30 秒で分かる役割

V4 が生み出した **完成物** を置く場所。設計パッケージ、生成された Repo 雛形、CompanyOS エクスポート、移行計画、引き渡しなど。

V3 `21_outputs/` を継承。

## 1. このrootが持つもの

- design_packages/ — 完成した設計書
- scaffolded_repos/ — 生成された Repo 雛形
- companyos_exports/ — CompanyOS に渡す接続情報
- generated_surfaces/ — UI 表示用派生ビュー
- migration_plans/ — V3 → V4 などの移行計画
- handoff_packages/ — 別 Repo / 別 AI への引き継ぎ
- quality_reports/ — 品質確認結果
- audit_reports/ — 既存 Repo 診断レポート（audit_existing_repo）
- retrofit_plans/ — 既存 Repo 改修計画（retrofit_existing_repo）

## 2. このrootが持たないもの

- 作業中のドラフト（→ `../20_workspace/`）
- target repo の業務正本
- 生 feedback / learning

## 3. File Map（MVP）

MVP では実成果物本体はまだ置かない。各カテゴリの住所（sub-dir）と README は用意し、実物は作業ごとに追加される。

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `design_packages/` | 設計書一式 | 空 |
| `scaffolded_repos/` | 生成 Repo 雛形 | 空 |
| `companyos_exports/` | CompanyOS への接続情報 | 空 |
| `generated_surfaces/` | UI 表示用 view | 空 |
| `migration_plans/` | 移行計画 | 空 |
| `handoff_packages/` | 引き継ぎ | 空 |
| `quality_reports/` | 品質確認結果 | 空 |
| `audit_reports/` | 既存 Repo 診断レポート | 空 |
| `retrofit_plans/` | 既存 Repo 改修計画 | 空 |

## 4. 読む順番

1. `README.md`
2. （実物が出てから）任意

## 5. 最低 acceptance

- 9 カテゴリの sub-dir が（空でも）役割が説明されている
- 業務正本本体は置かれていない
- 完成物には source_pin / 出自記録がある

## 6. 止める条件

- 業務正本本体が `21_outputs/` 内に置かれた
- 作業中のドラフトと完成物の区別が消えた
- 完成物が出自記録なしで置かれた

## 7. 関連 root

- `../20_workspace/` — 作業中
- `../06_build/` — 生成手段
- `../31_learning/` — 完成物への学び
