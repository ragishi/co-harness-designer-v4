# 00_promotion_protocol.md — 昇格手続き

## 役割

`30_feedback/raw/` から `31_learning/` 内の各層、そして `00`-`07` の正式設計への **昇格手続き** を定義する。

V3 の signal registry の lifecycle と 4-AND 昇格門を継承。

## 持つもの

- 5 段階の昇格パス（signals → patterns → candidates → accepted / rejected）
- 4-AND 昇格門
- 各段階の判定者と判定タイミング

## 持たないもの

- 個別 signal / pattern / candidate の本文（→ 各 sub-dir）
- 業務正本

---

## 5 段階の昇格パス

```text
30_feedback/raw/{YYYY-MM}.md     ← 生の観測
       ↓ 再発 3 回以上
31_learning/signals/{signal_id}.md   ← 兆候
       ↓ 冷却 7 日 + 抽象化
31_learning/patterns/{pattern_id}.md ← パターン
       ↓ grader pass
31_learning/candidates/{candidate_id}.md ← 採用候補
       ↓ boundary check pass + saku 6 択判断
31_learning/accepted/{accepted_id}.md  または rejected/{rejected_id}.md
       ↓ accepted のみ
00 - 07 の正式設計に反映（contract / archetype / quality 等）
       ↓ rejected の場合
90_archive/migration_records/ に理由付き保管
```

## 4-AND 昇格門

各段階で **AND** で全部満たさないと先に進めない。

### Stage 1: raw → signals（兆候として認識）

| Condition | 内容 |
| --- | --- |
| 再発 ≥ 3 | 同じ事象が raw に 3 回以上 append されている |
| 別 entry | 別の日時 / 別の状況での再発（連続記録ではない） |

### Stage 2: signals → patterns（抽象化）

| Condition | 内容 |
| --- | --- |
| 冷却期間 ≥ 7 日 | signal を立ててから 7 日以上経過 |
| 抽象化可能 | 個別事象を超えてパターンとして言語化できる |

### Stage 3: patterns → candidates（採用候補）

| Condition | 内容 |
| --- | --- |
| grader pass | pattern を他者（grader）が読んで妥当と判断 |
| 関連 contract / archetype 識別 | どこに反映するかが明確 |

### Stage 4: candidates → accepted（採用）

| Condition | 内容 |
| --- | --- |
| boundary check pass | 「これを採用すると壊れない」を構造で確認 |
| saku 6 択判断 | 採用 / 延期 / 修正 / 部分採用 / 却下 / hub 返却のいずれか |

candidate が **rejected** された場合は `rejected/` 配下に理由付きで保管。

## 各段階の判定者と判定タイミング

| Stage | 判定者 | タイミング |
| --- | --- | --- |
| Stage 1 | AI（grep + count） | 月次レビュー / 必要時 |
| Stage 2 | saku または delegate | 月次レビュー |
| Stage 3 | grader（AI / human） | candidate 提出時 |
| Stage 4 | saku | improvement card で 6 択判断 |

## accepted の反映先

| 影響範囲 | 反映先 |
| --- | --- |
| L0（root 構造） | `../00_foundation/04_decision_rules.md` の migration package 経由 |
| L1（原則・SSOT） | `../00_foundation/01_principles.md` 等を更新 |
| L2（contract / archetype） | `../02_contracts/` / `../04_archetypes/` 等を更新 |
| L3（file 追加） | 該当 tier に file 追加 |
| L4（section 内容） | 該当 tier の file を編集 |

## 関連ファイル

- `../30_feedback/raw/_no_curate_here.md`
- `../00_foundation/04_decision_rules.md`（DRR + L0–L4 + migration package）
- `../07_quality/30_critical_gates.md`（DRR Gate）

## 最低 acceptance

- 5 段階の昇格パスが図で読める
- 4-AND 昇格門が各 stage で表で読める
- 各段階の判定者とタイミングが明示されている

## 止める条件

- 昇格門の AND が OR に変更された
- raw → accepted を直接通す path ができた
- rejected が削除された
- saku 6 択判断が省略された
