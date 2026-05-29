---
id: workspace.experiments.v1
status: planned
owner: 20_workspace
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# experiments/ — 試行錯誤の場

## 役割

V4 設計プロセスにおける **試行錯誤・仮説検証・プロトタイプ** を置く場所。
active に移す前の探索段階、あるいは active に移さないまま終わる実験を受け持つ。
失敗した実験も含めて残し、「やってみたが使わなかった」記録として機能する。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## このフォルダが持つもの

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口（本 file） | ✓ |
| `{YYYY-MM}_{experiment_slug}/` | 個別実験フォルダ | — 後段 |

MVP 空 — 現状 entry なし

## このフォルダが持たないもの

- 完成物（→ `../../21_outputs/`）
- 業務正本
- 確定した設計作業（→ `../active/{slug}/`）
- raw 観測（→ `../../30_feedback/raw/`）

## MVP での扱い

本 folder は MVP ではまだ使わない（active 化しない）。最初の実験が始まったタイミングで実装する。

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 完成物や業務正本がここに置かれる
- 実験と正式設計作業の区別が曖昧になる

## 関連ファイル

- `../README.md`
- `../active/README.md` — 正式設計作業
- `../../30_feedback/raw/` — 実験から生まれた観測の記録先
