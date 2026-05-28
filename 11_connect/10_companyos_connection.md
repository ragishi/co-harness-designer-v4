---
id: connection.companyos.v1
status: active
owner: 11_connect
note: "V4 / CompanyOS / target repo / .companyos / UI の関係を初心者向けに説明する。"
---

# 10_companyos_connection.md — V4 と CompanyOS の関係（初心者向け）

## 役割

V4、CompanyOS、target repo、`.companyos/`、CompanyOS UI、それぞれの関係を、専門用語に頼らず説明します。

## 持つもの

- 5 主体の関係図と役割
- Repo Card / Workflow Lens / Member Work Lens の易しい説明
- 「もし CompanyOS UI が壊れたら何が起きるか」のシナリオ

## 持たないもの

- 個別 contract 本体（→ `../02_contracts/`）
- CompanyOS 側の UI 実装
- exporter の実装コード

---

## 全体図（イメージ）

```text
                    ┌──────────────────────────────┐
                    │  CompanyOS（Hub / Control Plane）│
                    │  会社の「総務・掲示板システム」      │
                    └──────────────┬───────────────┘
                                   │ projection（投影）
                                   ▼
        ┌──────────────────────────────────────────────────┐
        │                CompanyOS UI（表示画面）             │
        │                                                    │
        │   ┌──────────┐  ┌──────────────┐ ┌─────────────┐  │
        │   │Repo Card │  │Workflow Lens │ │Member Work  │  │
        │   │（名刺）  │  │（ホワイトボード）│ │Lens（TODO帳）│  │
        │   └─────▲────┘  └──────▲───────┘ └──────▲──────┘  │
        └─────────┼───────────────┼─────────────────┼────────┘
                  │               │                 │
                  │  source_pin（参照）              │
                  │                                 │
        ┌─────────┴───────────────┴─────────────────┴────────┐
        │ target repo（各ドメインの仕事部屋）                    │
        │  ├ 業務正本（記事本文 / WBS / 納品物 … ）             │
        │  └ .companyos/（接続口 = 玄関の掲示板）               │
        │     ├ surfaces/  ← UI への見せ方を定義               │
        │     ├ sync/      ← source_pin / freshness          │
        │     └ generated/ ← 再生成可能 cache                 │
        └──────────┬───────────────────────────────────────────┘
                   │
                   │ blueprint を伝播（archetype / contract / scaffold）
                   │
        ┌──────────┴───────────────────────────────────────────┐
        │ V4（co-harness-designer-v4）＝ この target repo を「産む」工場 │
        │  meta-blueprint（archetype / contract / metric / scaffold）   │
        │  を所有する。target の instance は持たない。                     │
        └──────────────────────────────────────────────────────────┘
```

---

## 各主体の説明（初心者向け）

### CompanyOS（Hub / Control Plane）

CompanyOS は **会社全体の総務・掲示板システム** です。

- 各 target repo の状況を UI 上でまとめて見せます
- UI のレイアウト、接続契約、権限（誰が何を見られるか）を所有します
- **業務正本は持ちません**。あくまで「見せる係」です

たとえば、総務が「全部署の今週の進捗を一覧で見たい」と言ったとき、情報を集めて掲示板に貼り出すのが CompanyOS の仕事です。

### V4（Repository Harness Factory）

V4（このリポジトリ）は **target repo を産む設計図工場** です。

- archetype（目的別の repo 原型）、contract（約束事）、scaffold（雛形）など、**meta-blueprint** を所有します
- target repo を実際に作るための型紙・設計書を置く場所です
- **target repo の instance（実物）は持ちません**。「型紙」だけ持ちます

工場が製品の設計図だけを持ち、実際の製品（target repo）は工場の外で動くイメージです。

### target repo（Work Source）

target repo は **実際に仕事をする部屋** です。

- note 制作（co-note-production）やクライアント案件など、ドメインごとに 1 つ存在します
- 記事本文、台本、納品物、WBS など **業務正本をすべて所有** します
- V4 の archetype に従って構成されていますが、正本管理は自分で行います

社内の各部署や担当者の「作業部屋」です。実際の成果物はここにあります。

### `.companyos/`（接続口）

`.companyos/` は **target repo 内の玄関口** です。

- target repo の正本ではありません（surface 定義 / source_pin / generated cache のみ）
- CompanyOS が「この repo は今どんな状態?」と読みに来たとき、ここを見ます
- 業務正本の一部を要約・参照して CompanyOS UI に表示するための定義を置きます

玄関に貼った「今週の業務ハイライト」掲示板です。中身の詳細は部屋（target repo）にあります。

### CompanyOS UI（投影先）

CompanyOS UI は **CompanyOS が描く表示画面** です。

- Repo Card / Workflow Lens / Member Work Lens などの画面を描画します
- **正本ではありません**。target repo の `.companyos/` から投影（projection）された表示です
- UI が壊れても、業務正本には何も影響しません

壁に映すプロジェクターの映像です。プロジェクターが壊れても、手元の資料（業務正本）は無傷です。

---

## Repo Card / Workflow Lens / Member Work Lens（初心者向け）

### Repo Card（名刺）

repo を **1 枚のカードで見せる UI** です。

- archetype アイコン（note repo / client repo など）
- 進行中の件数や最終更新日
- SPOKE.yml の基本情報（spoke_id / description / connection）

「この repo は何をしていて、今どんな状態か」を一目で分かるように見せます。名刺のように、最低限の情報を短くまとめたものです。

### Workflow Lens（ホワイトボード）

workflow の進行状況を **かんばん / レーン表示** で見せる UI です。

- レーン = 予定（todo）/ 進行中（in_progress）/ レビュー待ち（review）/ 完了（done）など
- 各タスクカードが現在どのレーンにいるかを一覧できます
- source_pin で target repo の workflow 状態を参照します

チームの作業ホワイトボードをデジタル化したものです。ホワイトボードを消しても、実際の作業記録（業務正本）は手元にあります。

### Member Work Lens（個人の TODO 帳）

owner（人）視点で **「今日やる仕事一覧」** を見せる UI です。

- task カードを owner で絞り込んだ view
- 「自分が担当しているタスクだけ見たい」ときに使います
- 複数 target repo にまたがるタスクも一覧できます

個人の TODO 手帳を CompanyOS が自動でまとめてくれるイメージです。手帳の元データ（業務正本）は各 target repo にあります。

---

## もし CompanyOS UI が壊れたら何が起きるか

V4 の根本原則（P0）は **「Repo = SSOT、UI = 投影」** です。

```text
【UI が壊れたとき】

  CompanyOS UI ← 表示が消える（影響あり）
       ↑
   projection
       ↑
  .companyos/generated/ ← cache が消えるだけ
       ↑
   source_pin
       ↑
  target repo 業務正本 ← 無傷（まったく影響なし）
```

- target repo の業務正本は完全に無傷です
- `.companyos/generated/` の cache が消えるだけで、source_pin から再生成できます
- CompanyOS UI が復旧すれば、再度 projection して表示が戻ります

**UI を壊しても業務は止まらない。これが V4 設計の核心です。**

プロジェクターが壊れても、手元の資料は残ります。修理が終わればまた映し出せます。

---

## 関連ファイル

- `00_connection_policy.md` — 接続方針（役割分担・方向性の要点）
- `../00_foundation/02_ssot_authority_map.md` — 3 所有者地図
- `../01_meaning_model/10_entities.md` — Repo / Surface / Lens entity 定義
- `../02_contracts/40_surface_contract.md` — surface 詳細契約
- `../06_build/scaffolds/companyos_interface/` — `.companyos/` 雛形

---

## 最低 acceptance

- 5 主体（CompanyOS / V4 / target repo / .companyos / UI）の役割が初心者にも読める
- Repo Card / Workflow Lens / Member Work Lens の易しい説明がある
- 「UI が壊れても業務正本は無傷」が明示されている
- 図と文章の両方で関係を示している

## 止める条件

- 業務正本が UI / `.companyos/` に侵入する記述がある
- direct writeback を許可する記述がある
- 5 主体の役割が混同される表現がある
