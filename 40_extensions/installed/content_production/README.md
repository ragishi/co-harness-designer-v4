---
id: extension.installed.content_production.v1
status: planned
owner: 40_extensions
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# content_production/ — 記事・動画・投稿制作 core extension

## 役割

note / YouTube / SNS 系 archetype が共通して必要とする**コンテンツ制作プロセスの core 機能**を提供する extension。
企画・執筆・編集・レビュー・校正・素材管理など、制作ワークフローの共通部分を担う。
各 archetype は `depends_on: content_production` を宣言し、メディア固有の拡張を上乗せする。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
note / youtube / sns いずれかの archetype が `depends_on: content_production` を宣言し、admission_criteria を満たしたタイミングで本格実装する。

## このフォルダが持つもの（後段で本格実装する内容）

- 制作フロー定義（企画 → 執筆 → 編集 → 完成）
- 共通コンテンツステータス enum
- 素材管理・バージョン管理のルール
- 各メディア共通の quality 基準

## このフォルダが持たないもの

- メディア固有の処理（YouTube の動画編集、SNS の文字数制限など → 各 archetype）
- 公開処理（→ `../publish_pipeline/`）
- archetype 定義（→ `../../../04_archetypes/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- メディア固有処理が content_production に混入した
- extension が archetype を参照し始めた（一方向ルール違反）

## 関連ファイル

- `../README.md` — installed 全体
- `../publish_pipeline/` — 公開処理 extension
- `../../00_extension_policy.md` — 一方向依存ルール
