---
id: quality.archetype_quality.v1
status: planned
owner: 07_quality
note: "住所と役割確保のための stub。本格実装は後段。"
---

# 20_archetype_quality.md — archetype 別品質

## 役割

各 archetype が `10_common_quality.md` の共通 9 項目に **加えて** 満たすべき固有品質を定義する。

**planned stub であり、後段で本格実装する。** MVP では `note_production_repo` と `client_repo` の 2 archetype のみ薄く触れ、残り 6 archetype は後段と明示する。

## MVP での扱い

本 file は MVP では active 化しない。stub として「archetype 別品質の住所」を確保する。本格実装は各 archetype の運用実績が積まれた後段で行う。関連既存 file: `10_common_quality.md`（共通品質の正本）。

## 共通品質との関係

archetype 別品質は common quality を **上書きしない**。

- `10_common_quality.md` の 9 項目は全 archetype で必ず満たす
- 本ファイルの項目は common quality に **加えて** 満たす固有条件
- 優先度は common quality > archetype 別品質

---

## MVP 対象 archetype（薄く触れる）

### note_production_repo（記事制作リポジトリ）

共通 9 項目に加えて概要レベルで想定される固有品質（後段で詳細化）:

1. **記事ライフサイクル追跡**: draft / review / published の状態が SSOT で追える
2. **コンテンツ正本保護**: 記事本文が `.companyos/` に混入していない
3. **公開先 pointer**: 公開 URL / platform への参照が正本 Markdown に pin されている
4. **レビュー記録**: 編集レビューの記録が feedback loop に乗っている
5. **SEO / タグ正本**: タグ・カテゴリが JSON ではなく Markdown frontmatter に正本化されている

### client_repo（クライアント業務リポジトリ）

共通 9 項目に加えて概要レベルで想定される固有品質（後段で詳細化）:

1. **クライアント境界**: クライアント固有情報が他クライアントの正本に混入しない
2. **納品物 source pin**: 納品物 generated のすべてに元 Markdown が追える
3. **契約・依頼正本分離**: 契約書と実作業正本が別ファイルに分離している
4. **期限 / milestone 追跡**: 期限が単一箇所で管理されている

---

## 後段 archetype（内容は書かない）

以下 6 archetype は後段で実装する。名前と住所の確保のみ。

| archetype | 後段で書く内容の概要 |
| --- | --- |
| `project_progress_repo` | プロジェクト進捗の状態 SSOT / milestone 品質 |
| `sns_operations_repo` | SNS 投稿スケジュール / platform 正本分離 |
| `youtube_ops_repo` | 動画メタ情報 / サムネイル pointer / 公開状態 |
| `workflow_ops_repo` | workflow 定義 SSOT / 自動化 source pin |
| `prompt_repo` | prompt 正本 / バージョン管理 / テスト結果追跡 |
| `design_system_repo` | component 正本 / token SSOT / UI not SSOT 強化 |

## 持つもの

- common quality との関係定義
- MVP 2 archetype の固有品質（概要レベル 3-5 項目）
- 後段 6 archetype の住所と後段宣言

## 持たないもの

- 後段 6 archetype の固有品質本文（→ 後段）
- common quality の上書き
- archetype 判定ロジック（→ `04_archetypes/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- common quality を上書きする項目が追加された
- 後段 6 archetype に詳細な品質基準を書き始めた

## 関連ファイル

- `README.md`
- `10_common_quality.md`
- `30_critical_gates.md`
- `../04_archetypes/`
- `00_quality_map.md`（planned）
