---
id: workspace.2026-05-note-production-pilot.08_handoff.v1
status: active
slug: 2026-05-note-production-pilot
handoff_to: Phase 3 実装者（人間 / AI）
---

# 08_handoff.md — 実装者への引き渡し

## 役割

ここまでの設計（00-07）を、Phase 3 の実装者が **そのまま実行できる形** にまとめる。

## 持つもの

- 0-7 のサマリ
- Phase 3 で実装者が行う作業の step-by-step 手順
- 完了判定（acceptance）
- 失敗時の取り扱い

## 持たないもの

- target repo（`co-note-production`）の業務正本
- 個別 surface の中身（→ 06、Phase 3 で実装者が `co-note-production/.companyos/` に書き起こす）

---

## サマリ（00-07 を 1 ページに圧縮）

### 何をするか（00, 01）

- `co-note-production` を最初の projected target repo として `.companyos/` interface を追加する
- V4 内には設計パッケージのみ、target 側への実装は Phase 3

### どの archetype か（02）

- `archetype.note_production_repo.v1`
- 必須 module: `content_production`, `publish_pipeline`, `feedback_loop`
- 禁止 module: `client_ops`

### 正本はどこか（03）

- 記事本文 / draft / meta は target の `20_workspace/articles/{slug}/`（業務正本）
- workflow 定義は target の `02_workflows/note_article_production.md`
- `.companyos/` は **投影のみ**、正本ではない

### どんなディレクトリか（04）

- 既存 root を触らず `.companyos/` を 1 つ追加（Common Core 9 entries 完成）
- `.companyos/` 内に 10 file（README / manifest / surfaces 3 / sync 3 / generated 1）

### 何を契約に使うか（05）

- active: `contract.repo.v1`, `contract.workflow.v1`, `contract.surface.v1`, `contract.markdown.v1`, `contract.mnp_surface.v1`
- planned stub: `contract.writeback.v1`（書き戻しを禁止する規約として参照）

### 何を表示するか / しないか（06）

- 表示する: repo メタ / 進行 status / next_action / source_path / 月次公開本数
- 表示しない: 記事本文 / draft / 未公開メモ / 個人感想

### 何で合格か（07）

- Common Quality 9 項目 + archetype 別品質 + 全 Critical Gates pass + acceptance 10/10

---

## Phase 3 実装手順（step-by-step）

> **重要**: 本 pilot 設計の Phase 3 適用は、V4 とは**別の作業セッション / 別の repo (`co-note-production`)** で実施する。
> 以下は実装者（人間 / AI）が `co-note-production` で行う作業の指示書。

### Step 0: 前提確認

```text
- `co-note-production` repo をチェックアウト
- 現在の Common Core を確認（README / SPOKE.yml / 7 root directory）
- `.companyos/` が **未存在**であることを確認
- V4 (`co-harness-designer-v4`) の以下を参照可能にしておく:
    - 04_archetypes/repo/note_production_repo.md
    - 06_build/scaffolds/companyos_interface/
    - 02_contracts/10_repo_contract.md
    - 02_contracts/40_surface_contract.md
    - 02_contracts/70_markdown_contract.md
    - 02_contracts/80_mnp_surface_contract.md
    - 03_status_metrics/10_workflow_status.md
    - 07_quality/30_critical_gates.md
```

### Step 1: 新ブランチ作成

```text
git checkout main
git pull origin main
git checkout -b feat/companyos-interface-scaffold
```

### Step 2: `.companyos/` 雛形を copy

V4 の `06_build/scaffolds/companyos_interface/` を `co-note-production/.companyos/` にコピーする。

> **環境前提**: 以下のコマンドは `co-harness-designer-v4` と `co-note-production` が **同一親 directory に sibling として存在する** ことを前提とする（例: 両方とも `/Users/saku/` 直下）。パスは実環境に合わせて調整すること。

```text
cp -R co-harness-designer-v4/06_build/scaffolds/companyos_interface/ \
      co-note-production/.companyos/
```

### Step 3: 雛形を実 source_pin で埋める

各 file を `co-note-production` 固有の内容に書き換える。

#### 3-1. `.companyos/README.md`
- 「接続口宣言。`co-note-production` の業務正本は通常 directory に置く。`.companyos/` は投影のみ」
- 関連 contract への ID 参照（雛形の表をそのまま採用）

#### 3-2. `.companyos/manifest.md`（Markdown 正本）
- `05_contract_design.md` の「manifest.md の最低項目」テンプレに沿う
- spoke_id: `spoke.note-production`
- archetype: `archetype.note_production_repo.v1`
- expose する 3 surface
- visibility: 業務正本は do_not_expose

#### 3-3. `.companyos/manifest.yml`（最小限の機械読み版）
- `05_contract_design.md` の YAML 例をそのまま採用
- `manifest.md` と整合する

#### 3-4. `.companyos/surfaces/repo_card.surface.md`
- `06_surface_design.md` の Surface 1 仕様に沿う
- 表示要素: repo 名 / archetype / version / 進行中 workflow 数 / 進行中 task 数 / 月次公開本数 / freshness
- source_pin: `../../README.md`, `../../SPOKE.yml`, `../../20_workspace/articles/*/meta.md`, `../../99_publish_history/{YYYY-MM}.md`
- MNP block は **書かない**

#### 3-5. `.companyos/surfaces/workflow_lens.surface.md`
- `06_surface_design.md` の Surface 2 仕様に沿う
- lane: planned / active / review_needed / publish_ready / published / learning
- source_pin: `../../02_workflows/note_article_production.md`, `../../20_workspace/articles/*/meta.md`
- MNP block は **書かない**

#### 3-6. `.companyos/surfaces/member_work_lens.surface.md`
- `06_surface_design.md` の Surface 3 仕様に沿う
- owner 別 active task list
- source_pin: `../../20_workspace/articles/*/meta.md`
- MNP block は **書かない**

#### 3-7. `.companyos/sync/source_pin.md`
- 3 surface 全要素の pin を集約
- 業務正本本体を**書かない**（pointer のみ）

#### 3-8. `.companyos/sync/freshness.md`
- 既定 cadence（`co-harness-designer-v4/06_build/scaffolds/companyos_interface/sync/freshness.md` を参照）
- `co-note-production` 固有の cadence 上書きは MVP では行わない

#### 3-9. `.companyos/sync/generated_from.md`
- 雛形（出自記録フォーマット）をコピー
- 実 generated 物は MVP では作らないため、雛形のまま

#### 3-10. `.companyos/generated/README.md`
- 「再生成可能 cache、手動編集禁止」明記
- 実 cache は空

### Step 4: `co-note-production/SPOKE.yml` を更新

既存 `SPOKE.yml` に以下を追記（既存項目は維持）：

```yaml
archetype: archetype.note_production_repo.v1
mvp_modules:
  - content_production
  - publish_pipeline
  - feedback_loop
forbidden_modules:
  - client_ops
```

### Step 5: Critical Gates 自己 check

`co-harness-designer-v4/07_quality/30_critical_gates.md` の項目を全て確認：

- [ ] `.companyos/` 内に業務正本が存在しない
- [ ] 3 surface 全てが source_pin を持つ
- [ ] manifest.md / manifest.yml が整合
- [ ] generated/ は README のみ
- [ ] MNP block を書いていない
- [ ] Common Core 9 entries 揃っている

### Step 6: `30_feedback/raw/{YYYY-MM}.md` に observation entry を追加

`co-note-production/30_feedback/raw/2026-XX.md`（target 側）に：

```markdown
### YYYY-MM-DD — V4 archetype 適用: note_production_repo

- V4 `06_build/scaffolds/companyos_interface/` を `.companyos/` にコピー適用
- 3 surface + sync + generated の雛形を実 source_pin で埋めた
- 業務正本は通常 dir のまま（コピーゼロ）
- MNP block は書かなかった（installed/ 昇格前）
- 関連 file: `.companyos/` 全 10 file, SPOKE.yml
```

### Step 7: PR 作成 + merge

```text
git add .companyos/ SPOKE.yml 30_feedback/raw/...
git commit -m "feat: add .companyos/ interface from harness-designer-v4 scaffold"
git push -u origin feat/companyos-interface-scaffold
gh pr create --base main --title "feat: add .companyos/ interface (note_production_repo archetype)"
gh pr merge <pr_url> --squash --delete-branch
```

### Step 8: V4 側へ feedback を戻す

V4 の `co-harness-designer-v4/30_feedback/raw/2026-05.md` に：

```markdown
### YYYY-MM-DD — Phase 3 完了: co-note-production への .companyos 適用

- Step 1-7 が完走したか / どこで詰まったか
- 雛形 → 実 source_pin 変換で迷ったポイント
- scaffold が `co-note-production` の既存 root と摩擦したか
- 次の archetype (client_repo) 適用前に直したい点
- 関連 file: `co-note-production/.companyos/`（全 10）
```

→ V4 の 30_feedback/raw に流すことで、Phase 4（学びループ）が起動する。

---

## 完了判定（acceptance）

`07_quality_plan.md` の **acceptance criteria 10 項目**を全て満たすこと。

## 失敗時の取り扱い

- Critical Gate に失敗 → 該当 file を修正、再 check
- 既存 root 構造に変更が発生 → **中断**、saku 確認
- 業務正本が `.companyos/` に混入 → **即座に削除**、再 check
- MNP block を誤って書いた → 削除（本 pilot では書かない方針）
- V3 (`co-harness-design-v3`) を編集しそうになった → **絶対停止**

## 関連ファイル

- 全 00-07
- `../../../04_archetypes/repo/note_production_repo.md`
- `../../../06_build/scaffolds/companyos_interface/`
- `../../../07_quality/30_critical_gates.md`
- `../../../CLAUDE.gate.md`
