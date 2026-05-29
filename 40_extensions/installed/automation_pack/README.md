---
id: extension.installed.automation_pack.v1
status: planned
owner: 40_extensions
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# automation_pack/ — 自動化 extension

## 役割

反復タスクの自動化・定期実行・通知・スケジューリングなど、**業務自動化の汎用機能** を提供する extension。
workflow_ops archetype が `depends_on` する想定だが、自動化ニーズを持つ他の archetype も利用可能。
extension は汎用的であり、特定ワークフローに強く結合しない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
workflow_ops archetype が `depends_on: automation_pack` を宣言し、admission_criteria を満たしたタイミングで本格実装する。

## このフォルダが持つもの（後段で本格実装する内容）

- 自動化ワークフロー定義テンプレート
- トリガー・スケジュール・条件分岐の共通スキーマ
- 通知・アラート設定パターン
- 自動化 quality チェック（暴走検知・ループ防止）

## このフォルダが持たないもの

- 特定業務ドメインのロジック（→ 各 archetype）
- CI/CD インフラ設定（→ `../../../../.github/`）
- archetype 定義（→ `../../../04_archetypes/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 汎用性を失い特定 archetype 専用になった
- extension が archetype を参照し始めた（一方向ルール違反）

## 関連ファイル

- `../README.md` — installed 全体
- `../../00_extension_policy.md` — 一方向依存ルール
- `../../admission_criteria.md` — 昇格条件
