# 10_common_quality.md — Common Quality（全 archetype 共通）

## 役割

V4 が産む全 target repo と V4 自身が **必ず満たす** 品質基準。

## 持つもの

- 9 項目の共通品質
- 各項目の判定方法
- archetype 別品質との関係

## 持たないもの

- archetype 固有の品質（→ `20_archetype_quality.md` 後段）
- 計算実装

---

## 9 項目の共通品質

| 項目 | 内容 | 判定 |
| --- | --- | --- |
| **SSOT** | 同じ正本が複数箇所に存在しない | grep で重複定義を検出 |
| **Markdown-first** | 正本が Markdown で読める | `*.json` / `*.yml` が正本扱いされていないか |
| **UI not SSOT** | HTML / UI 表示が正本になっていない | `.companyos/` / 表示用 file 内に業務正本がないか |
| **Source Pin** | generated 物の元が追える | `../06_build/scaffolds/.../sync/source_pin.md` 経由 |
| **Feedback Loop** | 使った学びが `30_feedback/` → `31_learning/` に流れる | 月次レビューで append あり |
| **Drift Check** | 不要な root / 概念が増えていない | DRR 5 質問の通過記録 |
| **Permission Boundary** | 書き戻し・編集権限が曖昧でない | `60_writeback_contract.md`（後段）参照 |
| **Generated not Canonical** | generated 物が正本扱いされていない | `.gitignore` 確認 + `generated/` policy 確認 |
| **MNP not SSOT** | MNP に業務正本が入っていない | MNP block を全文 grep して業務正本ワードチェック |

## 各項目の本文

### 1. SSOT

同じ意味の正本が 2 箇所にない。V3 P1「1 情報 1 住所」継承。

- 正本 1 + pointer N で表現
- 重複検出は `00_foundation/02_ssot_authority_map.md` に従う

### 2. Markdown-first

新規に情報を持つときは Markdown 第一候補。YAML / JSON は限定。

- 詳細：`../00_foundation/03_format_and_ui_policy.md`

### 3. UI not SSOT

UI / HTML / 投影先は正本にしない。P0 継承。

- 詳細：`../00_foundation/01_principles.md` P0

### 4. Source Pin

全 generated 物が `source_pin` を持つ。

- 詳細：`../06_build/scaffolds/companyos_interface/sync/source_pin.md`

### 5. Feedback Loop

使った学びが必ずどこかの `feedback.md` または `30_feedback/raw/` に流れる。

- 詳細：`../31_learning/00_promotion_protocol.md`

### 6. Drift Check

新規追加が DRR 5 質問を通っているか。

- 詳細：`../00_foundation/04_decision_rules.md`

### 7. Permission Boundary

UI → 業務正本の直接書き換え禁止。writeback は intent → 承認 → 正本更新。

- 詳細：`../02_contracts/60_writeback_contract.md`（後段）

### 8. Generated not Canonical

`generated/` 配下は再生成可能 cache。手動編集禁止。

- 詳細：`../06_build/scaffolds/companyos_interface/generated/README.md`

### 9. MNP not SSOT

MNP block は中間記法であり業務正本ではない。

- 詳細：`../02_contracts/80_mnp_surface_contract.md`

## archetype 別品質との関係

archetype 別品質（後段の `20_archetype_quality.md`）は **common quality を上書きしない**。

- common quality は全 archetype で **必ず満たす**
- archetype 別品質は common quality に **加えて** 満たす項目

## 最低 acceptance

- 9 項目が表で読める
- 各項目に判定方法がある
- archetype 別との関係が明示されている

## 止める条件

- common quality 9 項目のいずれかが「努力目標」になった
- archetype 別が common を上書きしている
- 判定方法のない品質項目が追加された

## 関連ファイル

- `30_critical_gates.md`
- `../00_foundation/01_principles.md`
- `../CLAUDE.gate.md`
