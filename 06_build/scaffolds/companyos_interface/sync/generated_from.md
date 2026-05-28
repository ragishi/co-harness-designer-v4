---
id: sync.generated_from.scaffold.v1
status: scaffold
note: "雛形。target repo にコピーして generated 物の出自を記録する。"
---

# generated_from.md（雛形）

## 0. 目的

`generated/` 配下のすべての物が **どの source_pin / どの exporter / どの commit から作られたか** を記録する。

「再生成可能」を構造で保証するために必要。

## 持つもの

- generated path 別の出自履歴
- 使った exporter と version
- 元 commit / branch

## 持たないもの

- 業務正本本体
- exporter の実装コード

---

## 記録形式

各 generated 物について：

```text
generated_path: {path}
exporter:      {exporter_id_with_version}
source_pins:
  - {source_pin_path}
source_commit: {sha or branch}
generated_at:  {ISO datetime}
```

例：

```text
generated_path: generated/repo_card.html
exporter:      exporter.repo_card.v1
source_pins:
  - ../../README.md
  - ../../SPOKE.yml
source_commit: a1b2c3d (main)
generated_at:  2026-05-28T14:00:00+09:00
```

## 再生成手順

```text
1. source_pin 側の file を確認
2. 使う exporter（id + version）を確認
3. exporter を実行
4. generated path に書き出す
5. このファイルに記録を append
```

## 最低 acceptance

- 全 generated 物が出自記録を持つ
- exporter id + version が記録されている
- source_commit が記録されている

## 止める条件

- 出自記録のない generated 物がある
- 手動編集した generated 物がある
- 出自記録が消されている

## 関連ファイル

- `source_pin.md`
- `freshness.md`
- `../generated/README.md`
