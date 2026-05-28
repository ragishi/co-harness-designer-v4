---
id: policy.extension_admission.v1
status: active
owner: 40_extensions
---

# admission_criteria.md — 採用基準

## 役割

`proposals/` から `installed/` に昇格させる、または新規 extension を受け入れる時の **採用基準** を定義する。

V3 の 11 質問 admission gate を継承・簡素化。

## 持つもの

- 11 admission 質問
- 4-AND 昇格門との関係
- proposal → installed のフロー

## 持たないもの

- 個別 extension の本文
- 採用後の運用ルール（→ `00_extension_policy.md`）

---

## 11 Admission 質問

新規 extension を `proposals/` に受け入れる際、または `installed/` に昇格させる際、以下に答える：

```text
Q1: この機能は core ではなく extension であるべきか？
Q2: 既存の archetype / contract で表現できないか？
Q3: 観察 3 回以上の再発があるか？
Q4: どの archetype が depends_on するか？
Q5: 業務正本を持たない構造か？
Q6: extension は archetype を知らない一方向構造か？
Q7: 失敗を 3 行で articulate できるか？
Q8: cost < value か？
Q9: 削除しても archetype 側の解除で対応できる構造か？
Q10: Markdown-first 原則を守るか？
Q11: MNP / JSON / generated を正本にしない構造か？
```

すべて Yes でなければ受け入れない（AND）。

## 4-AND 昇格門との関係

`proposals/` → `installed/` への昇格は、`../31_learning/00_promotion_protocol.md` の Stage 4（candidates → accepted）と同等の門を通る：

| 4-AND 門 | extension での意味 |
| --- | --- |
| 再発 ≥ 3 | proposal が 3 archetype 以上で参照された |
| 冷却 ≥ 7 日 | proposal として 7 日以上 pilot した |
| grader pass | 11 質問すべて Yes |
| boundary check pass | 「これを installed にしても壊れない」を確認 |

## proposal → installed のフロー

```text
1. extension の発想を 30_feedback/raw/ に append
2. 再発 3 回以上を確認
3. proposal として proposals/{extension_name}/ を作成
4. README + feedback + 必要 file（when_to_use / notation_rules / contract / examples）を書く
5. 7 日以上 pilot
6. 11 admission 質問に答える
7. 4-AND 昇格門を通る
8. saku 6 択判断
9. installed/{extension_name}/ に昇格（移動）
10. 90_archive/migration_records/ に経緯を記録
```

## 関連ファイル

- `00_extension_policy.md`
- `../31_learning/00_promotion_protocol.md`
- `../00_foundation/04_decision_rules.md`

## 最低 acceptance

- 11 質問が表で読める
- 4-AND 昇格門との対応が明示されている
- proposal → installed のフローが 10 step 以内で書ける

## 止める条件

- 11 質問の AND が OR に変更された
- 昇格 step を skip した
- proposal の段階を経ずに installed に直接書かれた
