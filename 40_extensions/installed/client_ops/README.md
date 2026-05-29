---
id: extension.installed.client_ops.v1
status: planned
owner: 40_extensions
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# client_ops/ — クライアント業務 extension

## 役割

クライアント管理・案件管理・コミュニケーション記録など、**client 系 archetype が必要とする業務機能** を提供する extension。
client_repo archetype が `depends_on` する想定。
MVP では未 install（archetype 側で `depends_on` が宣言されるまで作らない）。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
client_repo archetype が `depends_on: client_ops` を宣言し、かつ admission_criteria を満たしたタイミングで本格実装する。

## このフォルダが持つもの（後段で本格実装する内容）

- クライアント管理ワークフロー定義
- 案件ステータス管理スキーマ
- コミュニケーション記録テンプレート
- 使用条件・制約・止める条件

## このフォルダが持たないもの

- archetype 定義（→ `../../../04_archetypes/`）
- archetype への参照・依存（一方向ルール：extension は archetype を知らない）
- proposals 段階の pilot 手順（→ `../../proposals/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- extension が特定 archetype を参照し始めた（一方向ルール違反）
- admission 未完了で実装が始まった

## 関連ファイル

- `../README.md` — installed 全体
- `../../00_extension_policy.md` — 一方向依存ルール
- `../../admission_criteria.md` — 昇格条件
