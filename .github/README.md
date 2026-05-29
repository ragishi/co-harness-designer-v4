---
id: tooling.github.v1
status: planned
owner: .github
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# .github/ — GitHub 設定

## 役割

GitHub が利用する**ワークフロー・PR テンプレート・Issue テンプレート**の置き場（将来）。
CI/CD、自動チェック、コントリビューションガイドラインなどを管理する。
V4 の設計正本・業務正本はここには置かない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本フォルダは MVP では空（`.gitkeep` のみ）。
GitHub Actions や PR テンプレートが必要になったタイミングで追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- GitHub Actions ワークフロー定義（将来 `workflows/`）
- PR テンプレート（将来 `PULL_REQUEST_TEMPLATE.md`）
- Issue テンプレート（将来 `ISSUE_TEMPLATE/`）
- コントリビューションガイドライン（将来 `CONTRIBUTING.md`）

## このフォルダが持たないもの

- V4 設計正本（→ `../CLAUDE.md`、`../CLAUDE.gate.md`）
- Claude Code 設定（→ `../.claude/`）
- Codex 設定（→ `../.codex/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- V4 の設計正本がここに置かれた

## 関連ファイル

- `../CLAUDE.md` — V4 起動 router（正本）
- `../.claude/README.md` — Claude Code 設定
- `../.codex/README.md` — Codex 設定
