---
id: archetype.optional_modules.v1
status: active
owner: 04_archetypes
note: "目的別に追加する Optional Modules 8 種の初学者向け説明。archetype と extension の関係は 00_archetype_framework.md / 40_extensions/00_extension_policy.md。"
---

# 20_optional_modules.md — Optional Modules（目的に応じて足す部品）

## 役割

archetype が depends_on する Optional Module の説明です。Common Core に**追加**される機能パックで、archetype の目的に合わせて選択します。

## 持つもの

- 8 Optional Modules それぞれの「いつ使うか / 追加 file 例 / 使わない方がよい場合 / 関連 archetype」
- module と archetype の関係（一方向）

## 持たないもの

- Common Core の説明（→ `10_common_core.md`）
- archetype 本体（→ `repo/`）
- extension の installed 実体（→ `../40_extensions/installed/`、MVP では空）
- module の実装コード

---

## 8 modules 一覧（先に全体像）

| module | 一言 | 主な利用 archetype |
| --- | --- | --- |
| `project_management` | WBS と milestone を扱う | project_progress / client |
| `client_ops` | クライアント別管理 | client |
| `content_production` | 制作物の core ループ | note / youtube / sns |
| `publish_pipeline` | 公開準備 + 公開後フォロー | note / youtube / sns |
| `analytics_ops` | KPI / 反応分析 | sns / youtube / publish 後 |
| `automation_pack` | scripts / exporters / generators | advanced（autonomy が必要） |
| `prompt_ops` | Prompt 正本管理 | prompt |
| `design_system_ops` | UI token / component | design_system |

---

## 1. project_management

### いつ使うか

複数 task が並行して走り、それぞれに期限・担当者・依存関係がある場合に使います。たとえば「クライアント案件が 3 件同時進行している」「プロダクトリリースまでのタスクを milestone 単位で管理したい」といったシーンです。WBS を Markdown で書き、CompanyOS 上で進捗を可視化したいときに選びます。

### 追加されるフォルダ・ファイル例

```text
{target-repo}/
├── 02_workflows/
│   └── project_management.md       # WBS / milestone workflow 本体
├── 20_workspace/
│   └── projects/
│       └── {project_slug}/
│           ├── wbs.md              # タスク一覧と status
│           ├── milestone.md        # milestone 定義と期限
│           └── progress_log.md     # 進捗の記録
```

### 使わない方がよい場合

- 単発の記事制作や個人の学習 repo など、タスクが 1 本道で完結する場合は不要です。
- note 制作のみが目的の repo に入れると、管理コストが運用負荷を上回ります。

### 関連 archetype

- `client_repo` — 必須 module として宣言（WBS と milestone が案件管理の core）
- `project_progress_repo`（将来）— 必須 module として宣言
- `note_production_repo` — 禁止ではないが通常不要（content_production で十分）

---

## 2. client_ops

### いつ使うか

クライアント案件を複数同時に抱えており、依頼元・契約・成果物・納品・請求をまとめて管理したい場合に使います。「クライアントが 3 社いて、それぞれの案件状態を一箇所で把握したい」「納品履歴と振り返りをクライアント単位で残したい」といったシーンです。

### 追加されるフォルダ・ファイル例

```text
{target-repo}/
├── 10_clients/
│   └── {client_slug}/
│       ├── meta.md                 # クライアント基本情報
│       ├── projects/
│       │   └── {project_slug}/
│       │       ├── brief.md        # 依頼内容
│       │       ├── wbs.md          # タスク分解
│       │       └── delivery_log.md # 納品履歴
│       └── archive/
└── 99_invoices/                    # 請求書 archive（visibility 制御）
```

### 使わない方がよい場合

- 記事制作や個人発信の repo には不要です（note_production_repo では禁止 module）。
- クライアントが 1 社のみで案件数も少ない場合は、project_management だけで十分なことが多いです。

### 関連 archetype

- `client_repo` — 必須 module（クライアント別管理の core）
- `note_production_repo` — 禁止 module（note 制作 repo は client 概念を持たない）
- `youtube_repo`（将来）— 通常不要

---

## 3. content_production

### いつ使うか

note 記事・YouTube 動画・SNS 投稿など、制作物を継続的に作り続ける repo に使います。「月 4 本以上 note を書く」「YouTube 動画を週 1 本ペースで制作している」「SNS 投稿を計画的に作りたい」といった場合です。企画 → 制作 → レビュー の core ループを回すための scaffold を追加します。

### 追加されるフォルダ・ファイル例

```text
{target-repo}/
├── 02_workflows/
│   └── content_production.md       # 制作 workflow 本体
├── 20_workspace/
│   └── drafts/
│       └── {slug}/
│           ├── meta.md             # 制作物の基本情報（タイトル / 媒体 / status）
│           ├── brief.md            # 企画メモ
│           └── draft.md           # 執筆中の本文
└── 10_assets/                      # 共通素材（画像 / 引用元）
```

### 使わない方がよい場合

- 制作物を作らない repo（クライアント管理のみ・学習ノートのみなど）には入れないでください。
- client_repo では禁止 module です（制作物は専用 repo に分離します）。

### 関連 archetype

- `note_production_repo` — 必須 module（記事制作の core ループ）
- `youtube_repo`（将来）— 必須 module
- `sns_repo`（将来）— 必須 module
- `client_repo` — 禁止 module

---

## 4. publish_pipeline

### いつ使うか

制作物を外部に公開する直前の最終確認（誤字チェック / SEO / OGP など）と、公開後のフォロー（反応確認 / リライト判断）まで一貫して管理したい場合に使います。「note を公開する前に毎回チェックリストを通している」「公開後 1 週間の反応を記録したい」といったシーンです。

### 追加されるフォルダ・ファイル例

```text
{target-repo}/
├── 02_workflows/
│   └── publish_pipeline.md         # 公開準備 → 公開後フォロー workflow
├── 21_outputs/
│   └── published/
│       └── {slug}/
│           ├── publish_meta.md     # 公開日 / URL / platform
│           └── post_review.md      # 公開後の反応メモ
└── 99_publish_history/             # 公開済み一覧（archive pointer）
```

### 使わない方がよい場合

- 外部公開を行わない内部管理系 repo（client_repo など）には不要です。
- content_production を使わない repo に単体で入れても機能しません（content_production とセットで使います）。

### 関連 archetype

- `note_production_repo` — 必須 module（公開準備と公開後フォローの実行体）
- `youtube_repo`（将来）— 必須 module
- `sns_repo`（将来）— 必須 module

---

## 5. analytics_ops

### いつ使うか

公開後のコンテンツに対して KPI を設定し、反応（PV / スキ / フォロワー増減など）を継続的に記録・分析したい場合に使います。「note の月次 PV を追いたい」「YouTube チャンネルの成長率を KPI で管理している」「どの投稿が効いているかを振り返りたい」といったシーンです。

### 追加されるフォルダ・ファイル例

```text
{target-repo}/
├── 02_workflows/
│   └── analytics_ops.md            # KPI 計測・分析 workflow
├── 20_workspace/
│   └── analytics/
│       ├── kpi_definition.md       # KPI の定義と目標値
│       ├── monthly/
│       │   └── {YYYY-MM}.md        # 月次計測結果
│       └── insights.md             # 分析メモ / 改善アクション
```

### 使わない方がよい場合

- 公開数が月 1 本以下など、分析するほどのデータが溜まらない初期段階では入れないほうがよいです。
- 外部公開を行わない repo（client_repo / prompt_repo など）には基本不要です。

### 関連 archetype

- `note_production_repo` — 推奨 module（publish 後の反応確認）
- `youtube_repo`（将来）— 必須 module
- `sns_repo`（将来）— 必須 module

---

## 6. automation_pack

### いつ使うか

定型作業を scripts / exporters / generators で自動化したい場合に使います。「ステータス集計を毎週 script で自動化している」「記事 meta を YAML から自動生成している」「複数 repo にまたがるデータを export してまとめている」といったシーンです。手動オペレーションのボトルネックが特定できたときに追加します。

### 追加されるフォルダ・ファイル例

```text
{target-repo}/
├── scripts/
│   ├── exporters/
│   │   └── export_status.py        # status 集計 exporter
│   ├── generators/
│   │   └── gen_meta.py             # meta 雛形生成
│   └── utils/
│       └── helpers.py
└── .companyos/
    └── automation/
        └── scheduled_tasks.md      # 定期実行の宣言
```

### 使わない方がよい場合

- 手動オペレーションが月数回しかない場合、script を書くコストのほうが高くなります。
- 運用が安定していない初期フェーズでは入れないでください。workflows が固まってから追加します。
- prompt_repo / design_system_ops repo など、制作・管理よりも「正本を維持する」ことが目的の repo には基本不要です。

### 関連 archetype

- `client_repo` — 推奨 module（案件横断の自動化 reminder / status 更新）
- `youtube_repo`（将来）— 推奨 module（動画メタデータ処理など）
- 初期フェーズの全 archetype — 通常不要

---

## 7. prompt_ops

### いつ使うか

Claude / GPT など AI に渡す Prompt を「正本」として管理したい場合に使います。「使い回す Prompt が増えてきて、どれが最新版か分からなくなってきた」「Prompt のバージョン管理と改善履歴を残したい」「チームで Prompt を共有・レビューしたい」といったシーンです。

### 追加されるフォルダ・ファイル例

```text
{target-repo}/
├── 02_workflows/
│   └── prompt_ops.md               # Prompt 管理 workflow
├── 20_workspace/
│   └── prompts/
│       └── {prompt_slug}/
│           ├── meta.md             # Prompt の目的 / 対象モデル / status
│           ├── prompt.md           # Prompt 本文（正本）
│           └── changelog.md        # 改善履歴
└── 21_outputs/
    └── prompt_eval/
        └── {prompt_slug}/
            └── {YYYY-MM-DD}_eval.md  # 評価メモ
```

### 使わない方がよい場合

- Prompt が 1〜2 個しかない場合は、20_workspace に直接置くだけで十分です。
- AI 活用が主目的でない repo（client_ops のみ / design_system のみなど）には入れないでください。

### 関連 archetype

- `prompt_repo`（将来）— 必須 module（Prompt 管理専用 repo の core）
- `note_production_repo` — Prompt を積極的に使うなら任意追加可

---

## 8. design_system_ops

### いつ使うか

デザイントークン（色 / フォント / spacing など）や UI コンポーネントを一元管理し、複数プロジェクトや媒体で一貫したビジュアルを保ちたい場合に使います。「ブランドカラーや typography を repo で管理している」「コンポーネント仕様を Markdown で定義して開発チームと共有している」といったシーンです。

### 追加されるフォルダ・ファイル例

```text
{target-repo}/
├── 02_workflows/
│   └── design_system_ops.md        # トークン更新・コンポーネント追加 workflow
├── 20_workspace/
│   └── design_system/
│       ├── tokens/
│       │   ├── color.md            # カラートークン定義
│       │   ├── typography.md       # フォント定義
│       │   └── spacing.md          # spacing 定義
│       └── components/
│           └── {component_slug}/
│               ├── spec.md         # コンポーネント仕様
│               └── usage.md        # 使用ガイド
└── 21_outputs/
    └── design_exports/             # Figma / CSS 変数など export 成果物
```

### 使わない方がよい場合

- 視覚デザインが発生しない repo（client_ops / analytics のみなど）には不要です。
- デザインリソースが 1 プロジェクト限定で再利用しない場合は、プロジェクト固有フォルダに直接置くほうが軽量です。

### 関連 archetype

- `design_system_repo`（将来）— 必須 module（デザインシステム専用 repo の core）
- その他 archetype — 通常不要（ブランド管理の必要が生じたときのみ追加）

---

## archetype と module の関係（一方向、再掲）

```text
archetype ──depends_on──> module
   note_production_repo            content_production
                                   publish_pipeline

   client_repo                     client_ops
                                   project_management
```

module は archetype を**知らない**。archetype が module を depends_on する一方向です。

---

## install / 昇格について

- MVP では `../40_extensions/installed/` は **空** です。
- 各 module の実体は今後 `../40_extensions/installed/{module}/` に置かれます（admission 後）。
- それまでは archetype が「必要 module」を宣言する設計上の参照のみです。

---

## 関連ファイル

- `00_archetype_framework.md` — archetype + module + extension の全体関係
- `10_common_core.md` — Common Core（Optional Module の base）
- `repo/note_production_repo.md` — module 利用例（note）
- `repo/client_repo.md` — module 利用例（client）
- `../40_extensions/00_extension_policy.md` — extension としての install 方針
- `../40_extensions/admission_criteria.md` — installed/ 昇格条件

---

## 最低 acceptance

- 8 modules が 4 要素揃っている
- archetype → module の一方向関係が明示されている
- 各 module の「使わない方がよい場合」が初心者でも読める

## 止める条件

- module が archetype を編集しようとした記述
- 9 個目以降の module を MVP で追加した
- module の実装コードを本 file に書き始めた
