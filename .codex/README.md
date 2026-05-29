---
id: tooling.codex.v1
status: planned
owner: .codex
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# .codex/ — Codex・AI runtime 用設定

## 役割

Codex および AI runtime が利用する**設定ファイル・ランタイム定義**の置き場（将来）。
`../AGENTS.md` が V4 における AI エージェントの動作原則を定義し、本フォルダはその runtime 設定を担う。
MVP では空（`.gitkeep` のみ）。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本フォルダは MVP では空（`.gitkeep` のみ）。
Codex / AI runtime の設定が必要になったタイミングで追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- Codex runtime 設定ファイル（将来）
- AI エージェント実行設定（将来）
- ランタイム固有の環境変数定義（将来）

## このフォルダが持たないもの

- V4 設計正本（→ `../CLAUDE.md`、`../AGENTS.md`）
- Claude Code 設定（→ `../.claude/`）
- GitHub Actions（→ `../.github/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- V4 の設計正本がここに置かれた

## 関連ファイル

- `../AGENTS.md` — AI エージェント動作原則（正本）
- `../.claude/README.md` — Claude Code 設定
- `../.github/README.md` — GitHub 設定
