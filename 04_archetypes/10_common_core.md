---
id: archetype.common_core.v1
status: active
owner: 04_archetypes
note: "全 archetype が必ず持つ共通骨格 9 entries の初学者向け説明。契約は 02_contracts/10_repo_contract.md。"
---

# 10_common_core.md — Common Core 9 entries（全 target repo 共通）

## 役割

V4 が産む全 target repo が必ず持つ共通骨格を、初心者にも分かる形で説明します。

「どの entry に何を置くか」を判断できるようにするための案内書です。契約本体（機械的な最低条件の定義）は `02_contracts/10_repo_contract.md` にあります。このファイルは archetype 視点の補完書であり、初学者向けの「なぜこの entry があるか」を伝えることが目的です。

## 持つもの

- Common Core 9 entries 各々の「やさしい説明 / 何を置くか / 何を置かないか / CompanyOS との関係 / 最低 acceptance」
- entry 間の関係（自然文）

## 持たないもの

- archetype 固有 root（→ 各 archetype の `repo/{name}.md`）
- contract 本体（→ `../02_contracts/`）
- 業務正本

---

## 9 entries 一覧（先に全体像）

| # | type | name | 一言 |
| --- | --- | --- | --- |
| 1 | root file | `README.md` | repo の入口・表札 |
| 2 | root file | `SPOKE.yml` | CompanyOS への接続契約 |
| 3 | root directory | `00_foundation/` | repo の憲法 |
| 4 | root directory | `20_workspace/` | 作業中のもの置き場 |
| 5 | root directory | `21_outputs/` | 完成物置き場 |
| 6 | root directory | `30_feedback/` | 生の観測 |
| 7 | root directory | `31_learning/` | 整理済み学び |
| 8 | root directory | `90_archive/` | 退役保管 |
| 9 | root directory | `.companyos/` | CompanyOS UI への接続口 |

ASCII イメージ：

```text
{target-repo}/
├── README.md             # root file (1)
├── SPOKE.yml             # root file (2)
├── 00_foundation/        # root directory (3)
├── 20_workspace/         # root directory (4)
├── 21_outputs/           # root directory (5)
├── 30_feedback/          # root directory (6)
├── 31_learning/          # root directory (7)
├── 90_archive/           # root directory (8)
└── .companyos/           # root directory (9)
```

**注意**: README.md・SPOKE.yml は root file（ディレクトリではない）なので「9 root」とは言いません。9 entries です。

---

## 1. README.md（root file）

### やさしい説明

repo の**表札**です。はじめてこの repo を開いた人が「この repo は何のためにあるのか」を30秒で把握できるように書きます。中に入る前に、まずここを読んでもらうための案内板です。

### 何を置くか

- repo の目的と一言説明
- 主な利用者（誰が使うか）
- ディレクトリ構成の簡易マップ
- よく使うコマンドや出発点へのリンク

### 何を置かないか

- 業務正本（記事本文、企画書、納品物）
- 詳細な操作手順（→ 各 directory の README に委譲）
- 設計思想の詳細（→ `00_foundation/` に委譲）

### CompanyOS との関係

CompanyOS には直接 expose されません。`.companyos/manifest.md` が CompanyOS への窓口になります。README.md は人間向けの案内書です。

### 最低 acceptance

- repo の目的が1文で書かれている
- ディレクトリ構成が一覧できる
- 読んだ人が「次にどこを見ればよいか」分かる

---

## 2. SPOKE.yml（root file）

### やさしい説明

CompanyOS への**引っ越し届**です。「この repo は CompanyOS のどの hub に接続します、archetype は何です」という接続契約を宣言します。この file があることで、CompanyOS が repo の存在を認識し、Surface 表示や同期ができるようになります。

### 何を置くか

```yaml
spoke_id: {target_repo_name}
version: {semver_or_baseline}
description: "..."
connection:
  hub: company-os
  mode: attached
archetype: {one_of_v4_archetypes}
mvp_archetypes:
  - {archetype_id}
```

最低限この 6 項目が必要です。

### 何を置かないか

- 業務ロジック・設定値
- secrets / credentials
- JSON 形式での記述（必ず YAML）
- archetype の設計思想の説明文（→ `00_foundation/` に委譲）

### CompanyOS との関係

CompanyOS がこの file を読み、repo を hub に「接続済み spoke」として登録します。`source_pin` の参照元のひとつにもなります。

### 最低 acceptance

- 6 必須項目（spoke_id, version, description, connection, archetype, mvp_archetypes）がすべてある
- YAML 形式で書かれている
- `connection.hub: company-os` が明示されている

---

## 3. 00_foundation/（root directory）

### やさしい説明

repo の**憲法**置き場です。「この repo は何のためにあるか、何をしない repo か、どんな原則で動くか」という根拠を書きます。ここを読めば repo の設計思想が分かります。作業するとき迷ったら、ここに戻ります。

### 何を置くか

- repo の目的・ミッション（`00_purpose.md` など）
- 設計原則・決定ルール（`04_decision_rules.md` など）
- 非交渉条件（絶対に変えない制約）
- 用語集・glossary

### 何を置かないか

- 業務正本（記事、企画書、納品物）
- 作業中ファイル（→ `20_workspace/`）
- workflow の手順書（→ archetype 固有 directory に委譲）
- フィードバックの記録（→ `30_feedback/`）

### CompanyOS との関係

直接 expose されません。設計思想は `.companyos/manifest.md` の description などを通じて間接的に伝わります。`00_foundation/` の内容は人間向けの内部文書です。

### 最低 acceptance

- repo の目的が1ファイル以上で書かれている
- 読めば「なぜこの repo が存在するか」が分かる

---

## 4. 20_workspace/（root directory）

### やさしい説明

**作業デスク**です。今まさに作業中のファイルを置きます。完成していないもの、検討中のもの、下書きはすべてここ。完成したら `21_outputs/` に移します。

### 何を置くか

- 執筆・制作中のファイル（下書き、ドラフト）
- 検討中の企画・構成メモ
- WIP（work-in-progress）フォルダ
- リサーチ中のメモ・素材

### 何を置かないか

- 完成・公開済みのもの（→ `21_outputs/`）
- フィードバック記録（→ `30_feedback/`）
- 学びの整理（→ `31_learning/`）
- 廃止・退役したもの（→ `90_archive/`）

### CompanyOS との関係

作業状況は `.companyos/surfaces/` の Surface 定義を通じて「進行中タスク」として表示される場合があります。ただし業務正本のファイル内容は expose されません（投影のみ）。

### 最低 acceptance

- WIP ファイルが `21_outputs/` と混在していない
- `20_workspace/README.md`（または最低限のナビ）がある

---

## 5. 21_outputs/（root directory）

### やさしい説明

**完成品の棚**です。`20_workspace/` で作り終えたものがここに移ります。公開・納品・承認済みのアウトプットを保管します。「完成した」と判断したタイミングで移動します。

### 何を置くか

- 公開済み記事・台本の最終版
- 納品済みのドキュメント・デザイン
- 承認済みの企画書
- リリース済みコンテンツのアーカイブ

### 何を置かないか

- 作業中・未完成のもの（→ `20_workspace/`）
- 廃棄・お蔵入りにしたもの（→ `90_archive/`）
- フィードバック（→ `30_feedback/`）

### CompanyOS との関係

`source_pin.md` で参照される「実績・成果物」の主要 source になります。`.companyos/surfaces/` の「最新アウトプット」表示の元データになります。

### 最低 acceptance

- `20_workspace/` の WIP と明確に分離されている
- 完成基準（いつ `21_outputs/` に移すか）が `00_foundation/` または README に書かれている

---

## 6. 30_feedback/（root directory）

### やさしい説明

**観測ノート**です。実際に作業して感じた違和感、うまくいかなかった点、「次はこうしたい」という気づきをそのまま書きます。整理しなくていい。生の観測を残すための場所です。

### 何を置くか

- 作業後の振り返りメモ
- 「ここが不便だった」「この手順は変えたい」の記録
- ユーザーからの指摘・感想
- 改善候補のアイデア（raw）

### 何を置かないか

- 整理・抽象化した学び（→ `31_learning/`）
- 業務正本・成果物（→ `21_outputs/`）
- ルール化・方針化したもの（→ `00_foundation/` に昇格させる）

### CompanyOS との関係

直接 expose されません。`30_feedback/` の内容は internal 扱いです。ただし `31_learning/` に昇格した学びは surface 経由で見えることがあります。

### 最低 acceptance

- `31_learning/` と明確に分離されている（「生の観測」と「整理済み学び」が混在しない）
- feedback が追記できる構造になっている

---

## 7. 31_learning/（root directory）

### やさしい説明

**整理済みの知恵棚**です。`30_feedback/` に書いた生の観測を整理・抽象化して、「次の作業で使えるパターン」にしたものを置きます。同じ失敗を繰り返さないための再利用知識置き場です。

### 何を置くか

- `30_feedback/` から昇格した学び（パターン化、抽象化済み）
- 繰り返し使えるチェックリスト
- 「このプロジェクトで学んだ原則」の整理
- `accepted/` / `pending/` などの昇格状態で管理

### 何を置かないか

- 生の観測・未整理メモ（→ `30_feedback/`）
- 業務正本・成果物（→ `21_outputs/`）
- ルール・方針として確定したもの（→ `00_foundation/` への昇格候補）

### CompanyOS との関係

整理された学びは `.companyos/surfaces/` 経由で「学習ログ」として表示される場合があります。重要な学びは `source_pin.md` に記録されることもあります。

### 最低 acceptance

- `30_feedback/` の raw メモと明確に区別されている
- 昇格した学びが「次の作業で実際に使える粒度」になっている

---

## 8. 90_archive/（root directory）

### やさしい説明

**退役倉庫**です。使わなくなったが「削除はしたくない」ものを保管します。過去の企画、お蔵入りになったコンテンツ、古いバージョンのファイルなど。「捨てるのは惜しいが、現役の作業エリアに置いておくと邪魔」なものの行き先です。

### 何を置くか

- 使用停止した企画・ドキュメント
- お蔵入りコンテンツ（制作したが未公開のまま廃棄）
- 旧バージョンの重要ファイル（参照したい可能性がある）
- 廃止されたワークフロー・テンプレート

### 何を置かないか

- 現役の作業ファイル（→ `20_workspace/`）
- 完成・公開済み成果物（→ `21_outputs/`）
- 削除すべきゴミファイル（archive ではなく削除する）

### CompanyOS との関係

原則として expose されません。退役コンテンツを CompanyOS の Surface に表示する必要はないためです。

### 最低 acceptance

- 現役ファイルと退役ファイルが混在していない
- `90_archive/` 内に置いた理由・日付が分かる命名または README がある

---

## 9. .companyos/（root directory）

### やさしい説明

CompanyOS への**接続口**です。この directory には「業務正本」は置きません。業務正本は `20_workspace/` や `21_outputs/` にあります。`.companyos/` は、その内容を CompanyOS の UI（Dashboard, Timeline など）に「投影」するための窓口だけを置く場所です。

比喩：`.companyos/` は「店の看板・メニュー表」で、実際の料理（業務正本）は厨房（`20_workspace/` 等）にあります。

### 何を置くか

```text
.companyos/
├── README.md         # 接続口の説明（「正本ではない」を明記）
├── manifest.md       # 何を expose するか（Markdown 正本）
├── manifest.yml      # manifest の機械読み版（最小限）
├── surfaces/         # UI 表示用 Surface 定義
│   └── *.surface.md
├── sync/             # 何から生成されたか
│   ├── source_pin.md
│   ├── freshness.md
│   └── generated_from.md
└── generated/        # 再生成可能 cache
    └── README.md
```

### 何を置かないか

| 置いてはいけないもの | 正しい置き場所 |
| --- | --- |
| 記事本文・台本 | `20_workspace/` / `21_outputs/` |
| WBS・タスク管理本体 | archetype 固有 directory |
| クライアント納品物 | `21_outputs/` |
| feedback 原本 | `30_feedback/` |
| learning 本文 | `31_learning/` |
| Prompt 正本 | archetype 固有 directory |

### CompanyOS との関係

`.companyos/` は全 9 entries の中で**唯一 CompanyOS に直接 expose される entry**です。`manifest.md` / `surfaces/` / `sync/` が CompanyOS hub によって読まれ、Dashboard に表示されます。`source_pin.md` は「どのファイルを参照して surface を生成したか」を記録し、freshness 管理に使われます。

### 最低 acceptance

- `README.md` に「接続口であり正本ではない」が明記されている
- `manifest.md`（Markdown 正本）が存在する
- `surfaces/` / `sync/` / `generated/` の 3 sub-dir が存在する
- 業務正本ファイルが `.companyos/` 内にない

---

## entry 間の関係（自然文）

**業務の流れ**：アイデアや下書きは `20_workspace/` で育て、完成したら `21_outputs/` に移します。使わなくなったものは `90_archive/` へ。

**学びの流れ**：作業中の気づきは `30_feedback/` に生のまま書き、十分整理されたら `31_learning/` に昇格させます。さらに原則化すべき学びは `00_foundation/` への昇格候補になります。

**CompanyOS への投影**：業務正本は常に `20_workspace/` / `21_outputs/` / archetype 固有 directory に置き、`.companyos/` はその「投影のみ」を担います。業務正本を `.companyos/` に直接置くことは禁止です。

**repo のアイデンティティ**：`README.md` と `SPOKE.yml` の2つの root file が repo の「表札」と「接続届」を担います。この2ファイルで「この repo は何者で、どこに接続するか」が決まります。

```text
[30_feedback] --(昇格)--> [31_learning] --(原則化)--> [00_foundation]

[20_workspace] --(完成)--> [21_outputs]
                               |
                            (投影)
                               ↓
                          [.companyos]
                               |
                            (expose)
                               ↓
                          CompanyOS UI
```

---

## 関連ファイル

- `../02_contracts/10_repo_contract.md` — Common Core の契約本体（機械的最低条件）
- `00_archetype_framework.md` — archetype framework（Common Core を含む archetype 全体）
- `20_optional_modules.md` — archetype 別に追加する部品（後段）
- `repo/note_production_repo.md` / `repo/client_repo.md` — Common Core の採用例

---

## 最低 acceptance

- 9 entries が 5 要素（やさしい説明 / 何を置くか / 何を置かないか / CompanyOS との関係 / 最低 acceptance）揃っている
- 業務正本と投影の分離が読める（特に `.companyos/` の説明）
- 初心者でも「どの entry に何を置くか」が判断できる

## 止める条件

- 9 entries 以外の entry を Common Core 扱いし始めた
- archetype 固有 root を Common Core として混入させた
- 業務正本を `.companyos/` に置く例が書かれた
