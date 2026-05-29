# 04_archetypes/ — 目的別 Repo 原型（★ V4 の中核）

## 0. 30 秒で分かる役割

V4 が**どんな Repo を作るか**を定義する。

ここが V4 の心臓。8 つの archetype（目的別 Repo 型）を提供し、target repo を生むときの設計図にする。

## 1. このrootが持つもの

- archetype framework（archetype とは何か）
- Common Core 定義（全 archetype 共通）
- Optional Modules 一覧
- 新 archetype 作成テンプレ（`_new_archetype_template/`）
- **設計上 archetype 候補は 8 つ。MVP では `note_production_repo` と `client_repo` の 2 つだけ実体化。残り 6 つは後段**
- workflow archetype（`workflows/`）— MVP では空（後段）

## 2. このrootが持たないもの

- target repo の業務正本
- 個別 instance 状態
- contract 本文（→ `../02_contracts/`）
- workflow 本文（→ target repo 側）

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | archetype への改善メモ | ✓ |
| `00_archetype_framework.md` | archetype とは何か（基礎） | ✓ |
| `10_common_core.md` | 全 archetype が持つ共通要素 | — 後段 |
| `20_optional_modules.md` | 目的別に追加する module | — 後段 |
| `_new_archetype_template/` | 新 archetype 作成用テンプレ | — 後段 |
| `repo/README.md` | repo archetype の入口 | ✓ |
| `repo/note_production_repo.md` | note 制作 archetype | ✓ |
| `repo/client_repo.md` | client 案件 archetype | ✓ |
| `repo/project_progress_repo.md` | プロジェクト進捗管理 archetype | — 後段 |
| `repo/sns_operations_repo.md` | SNS 運用 archetype | — 後段 |
| `repo/youtube_ops_repo.md` | YouTube 運用 archetype | — 後段 |
| `repo/workflow_ops_repo.md` | workflow 運用 archetype | — 後段 |
| `repo/prompt_repo.md` | prompt 管理 archetype | — 後段 |
| `repo/design_system_repo.md` | design system archetype | — 後段 |
| `workflows/README.md` | workflow archetype の入口 | — 後段 |
| `workflows/note_article_production.md` | note 記事制作 workflow 型 | — 後段 |
| `workflows/client_workflow.md` | client 案件 workflow 型 | — 後段 |
| `workflows/project_management.md` | project 進捗管理 workflow 型 | — 後段 |
| `workflows/research_to_content.md` | リサーチ → content workflow 型 | — 後段 |
| `workflows/sns_post_production.md` | SNS 投稿制作 workflow 型 | — 後段 |
| `workflows/youtube_video_production.md` | YouTube 動画制作 workflow 型 | — 後段 |

MVP では note と client の 2 archetype のみ。残りは使いながら追加。

## 4. 読む順番

1. `README.md`
2. `00_archetype_framework.md`
3. `repo/README.md`
4. `repo/note_production_repo.md`
5. `repo/client_repo.md`

## 5. 最低 acceptance

- archetype とは何かが framework で読める
- repo/ に 2 archetype 以上の定義がある
- 各 archetype に Common Core + 必須 module の宣言がある
- 各 archetype に「持つもの / 持たないもの」がある

## 6. 止める条件

- archetype に target repo の業務正本がコピーされた
- archetype が contract 本文を内包し始めた（ID 参照すべき）
- 新 archetype が `_new_archetype_template/` を通らず追加された

## 7. 関連 root

- `../02_contracts/10_repo_contract.md` — target repo 最低要件
- `../06_build/scaffolds/` — archetype の物理 scaffold
- `../07_quality/20_archetype_quality.md`（後段） — archetype 別品質
- `../40_extensions/installed/` — archetype が depends_on する extension
