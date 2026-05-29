---
id: tooling.claude.v1
status: planned
owner: .claude
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# .claude/ — Claude Code 用設定・拡張

## 役割

Claude Code が利用する**設定ファイル・コマンド定義・エージェント設定**の置き場。
将来的には `commands/`、`agents/`、`settings/` などのサブディレクトリを持つ。
V4 の正本はここには置かない。V4 の設計・原則は `../CLAUDE.md`、`../CLAUDE.gate.md` が担う。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本フォルダは MVP では空（`.gitkeep` のみ）。
Claude Code の設定・コマンド・エージェント定義が必要になったタイミングで追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- Claude Code カスタムコマンド定義（将来 `commands/`）
- Claude Code エージェント設定（将来 `agents/`）
- Claude Code 設定ファイル（将来 `settings/`）

## このフォルダが持たないもの

- V4 設計正本（→ `../CLAUDE.md`、`../CLAUDE.gate.md`）
- 業務正本・archetype 定義（→ 各正本の場所）
- Codex / GitHub Actions 設定（→ `../.codex/`、`../.github/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- V4 の設計正本がここに置かれた

## 関連ファイル

- `../CLAUDE.md` — V4 起動 router（正本）
- `../CLAUDE.gate.md` — 完了前検査（正本）
- `../.codex/README.md` — Codex 設定
- `../.github/README.md` — GitHub 設定
