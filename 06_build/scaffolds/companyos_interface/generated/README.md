---
id: generated.scaffold.v1
status: scaffold
note: "雛形。target repo にコピーして使う。このディレクトリは build パイプラインのみが書き込み可能。"
---

# generated/ — 再生成可能 cache

## 0. 目的

`.companyos/` 配下で **再生成可能な cache** を置く場所。

ここに置かれる物は：

- 全て source_pin から派生
- 全て手動編集禁止
- 全て削除しても再生成で復元可能

## 重要

**ここの中身は正本ではない**。

業務正本は target repo の通常 directory（`20_workspace/`, `21_outputs/`, `02_workflows/` など）にある。
ここはあくまで UI 表示用の派生キャッシュ。

## 置いてよいもの

- `repo_card.html` / `repo_card.json` — Repo Card 用 generated view
- `workflow_lens.html` / `.json` — Workflow Lens 用
- `member_work_lens.html` / `.json` — Member Work Lens 用
- exporter が生成した中間 file

JSON は generated cache としてのみ許可（正本にしない）。

## 置いてはいけないもの

- 業務正本（記事本文、台本、納品物）
- 手動編集した内容
- source_pin のない物
- 出自記録 (`../sync/generated_from.md`) のない物

## 再生成のルール

- 削除しても源 (`../sync/source_pin.md`) から再生成可能
- 出自は `../sync/generated_from.md` に記録
- 鮮度は `../sync/freshness.md` で管理

## 最低 acceptance

- 全 generated 物が source_pin を持つ
- 全 generated 物が `../sync/generated_from.md` に記録あり
- 業務正本本体が入っていない

## 止める条件

- 業務正本が入った
- 手動編集された物がある
- 出自記録のない物がある

## 関連ファイル

- `../sync/source_pin.md`
- `../sync/freshness.md`
- `../sync/generated_from.md`
- `../manifest.md`
