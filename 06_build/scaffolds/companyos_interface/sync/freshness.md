---
id: sync.freshness.scaffold.v1
status: scaffold
note: "雛形。target repo にコピーして freshness の運用方針を埋める。"
---

# freshness.md（雛形）

## 0. 目的

surface / generated 物の **鮮度（最後にいつ source_pin から再生成されたか）** を記録する。

UI 側で「この情報は何分前のものか」を判定するために使う。

## 持つもの

- 各 generated 物の last_generated_at
- 各 surface の last_synced_at
- 再生成の cadence（既定の更新頻度）

## 持たないもの

- 業務正本本体
- 生成失敗のスタックトレース（→ build パイプライン側）

---

## 既定 cadence

| 物 | 既定 cadence |
| --- | --- |
| `surfaces/*.surface.md` | repo 編集時（リアルタイムでなくよい） |
| `generated/repo_card.*` | 1 時間ごと または manual trigger |
| `generated/workflow_lens.*` | 15 分ごと または manual trigger |
| `generated/member_work_lens.*` | 15 分ごと または manual trigger |

これは推奨。target repo / archetype 別に上書き可能。

## 記録形式

```text
{generated_path} : last_generated_at = {ISO datetime}
{surface_path} : last_synced_at = {ISO datetime}
```

例：

```text
generated/repo_card.html : last_generated_at = 2026-05-28T14:00:00+09:00
surfaces/workflow_lens.surface.md : last_synced_at = 2026-05-28T13:45:00+09:00
```

## stale 判定

- generated が `last_generated_at` から既定 cadence の 2 倍を超えたら `stale`
- stale は UI 側で警告表示
- source_pin 側 file が更新されているのに generated が更新されていない場合も `stale`

## 最低 acceptance

- 既定 cadence が表で読める
- 記録形式の例が示されている
- stale 判定基準がある

## 止める条件

- last_generated_at が記録されていない generated 物がある
- stale を無視して generated を正本扱いしている
- cadence が「即時必須」になっている（リアルタイム要件は別問題）

## 関連ファイル

- `source_pin.md`
- `generated_from.md`
- `../manifest.md`
