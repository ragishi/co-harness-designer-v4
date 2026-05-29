# 00_archetype_framework.md — archetype framework

## 役割

archetype とは何か、どう構成するか、archetype 同士の関係を定義する。

## 持つもの

- archetype の定義
- Common Core（全 archetype 共通）
- Optional Module の考え方
- archetype と extension の関係
- 新 archetype 追加プロセス

## 持たないもの

- 個別 archetype の本文（→ `repo/{archetype}.md`）
- 個別 extension の本文（→ `../40_extensions/`）

---

## archetype とは何か

```text
Archetype
=
目的別 Repo の「型」
=
Common Core + Required Modules + Recommended Modules + Forbidden Modules + Quality Profile
```

V4 が **新しい target repo を産むときの設計図**であり、**既存 target repo を診断・改修するときの基準**でもある。

## archetype の 2 つの使い方

1. **新規 Repo 設計**（`new_repo`）
   - まだ存在しない target repo を作るための設計図として使う。
2. **既存 Repo 診断・改修**（`audit_existing_repo` / `retrofit_existing_repo`）
   - 既存 target repo が、その目的に対して十分な構造・品質・CompanyOS 接続口を持っているかを確認する基準として使う。

→ 作業モードの定義は `../00_foundation/05_operating_modes.md`。

## archetype の構成

各 archetype 定義（`repo/{name}.md`）は以下を持つ：

```markdown
---
id: archetype.{name}.v1
status: active | draft
owner: 04_archetypes
---

# {archetype_name}

## 目的
何のための repo か

## 必須 module
- module_id_1
- module_id_2

## 推奨 module
- module_id_3

## 禁止 module
- module_id_4（理由）

## 持つべき workflow
- workflow_id_1

## CompanyOS に表示するもの
（Surface の概要）

## CompanyOS に表示しないもの
（業務正本の保護対象）

## 関連 contract / quality
```

## Common Core（全 archetype が必ず持つ 9 entries）

**9 entries = 2 root files (README.md, SPOKE.yml) + 7 root directories**。README.md / SPOKE.yml は root file であり root ではないため、「9 root」とは呼ばない。

```text
{target-repo}/
├── README.md             # root file
├── SPOKE.yml             # root file
├── 00_foundation/
├── 20_workspace/
├── 21_outputs/
├── 30_feedback/
├── 31_learning/
├── 90_archive/
└── .companyos/
```

詳細は `../02_contracts/10_repo_contract.md`。

## Optional Module の考え方

Optional Module は **archetype に depends_on される機能 pack**。

| module | 何ができる | 主な利用 archetype |
| --- | --- | --- |
| `project_management` | WBS / 進捗 / milestone | project_progress / client |
| `client_ops` | クライアント案件管理 | client |
| `content_production` | note / YouTube / SNS 制作 | note / youtube / sns |
| `publish_pipeline` | 公開準備・公開後分析 | note / youtube / sns |
| `analytics_ops` | KPI / 反応分析 | sns / youtube |
| `automation_pack` | scripts / exporters / generators | （advanced） |
| `prompt_ops` | Prompt 管理 | prompt |
| `design_system_ops` | UI token / component | design_system |

module 本体は `../40_extensions/installed/{module}/`（MVP では未配置）に置く。

## archetype と extension の関係（一方向）

```text
archetype ──depends_on──> extension
   note_production_repo            content_production
                                   publish_pipeline
                                   feedback_loop (built-in)

   client_repo                     client_ops
                                   project_management
```

extension は archetype を**知らない**。archetype が extension を depends_on する一方向。

## 新 archetype 追加プロセス

1. `_new_archetype_template/` を `repo/{new_name}.md` にコピー
2. 必須 module / 推奨 module / 禁止 module を埋める
3. 持つべき workflow を宣言
4. DRR 5 質問を通す
5. governance review
6. `../31_learning/accepted/` を経由
7. `00_contract_map.md` 系に影響があれば contract 側も更新

## 最低 acceptance

- archetype の定義（Common Core + Modules + Workflow + Surface 範囲）が明確
- archetype が新規設計の設計図かつ既存診断・改修の基準であることが明示されている
- Common Core の 9 entries（2 root files + 7 root directories）が列挙されている
- Optional Module 一覧がある
- archetype と extension の一方向関係が明示されている

## 止める条件

- archetype が extension を変更しようとした（一方向の逆）
- 新 archetype が `_new_archetype_template/` を通らず追加された
- Common Core 9 entries のいずれかが欠けた

## 関連ファイル

- `repo/README.md`
- `../02_contracts/10_repo_contract.md`
- `../40_extensions/admission_criteria.md`（後段）
- `../00_foundation/04_decision_rules.md`（DRR）
