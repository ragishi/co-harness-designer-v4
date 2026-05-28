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

## Phase 3 実行条件（AI への絶対ルール）

> **AI への警告**: このファイルを読んだだけで Phase 3 を開始してはいけない。
> このゲートはサマリ・実装手順より**前**に配置されている — 実装文脈を読み込む**前**にここで止まること。

この handoff は Phase 3 実装者向けの指示書である。ただし、AI が「自然な次の一手」として勝手に Phase 3 を開始すると、**V4 とは別の repo (`co-note-production`) を編集することになる**。これは事故の典型パターン。

### Phase 3 を開始してよい条件

ユーザーが **明示的に target repo 適用を依頼した場合のみ**：

| 種別 | 例 |
| --- | --- |
| ◎ 明示承認（Phase 3 OK） | 「co-note-production に .companyos interface を適用して」 |
| ◎ 明示承認（Phase 3 OK） | 「Phase 3 として co-note-production 側を実装して」 |
| ◎ 明示承認（Phase 3 OK） | 「target repo への適用を開始して」 |
| ◎ 明示承認（Phase 3 OK） | 「note-production-pilot を実行して」 |
| ◎ 明示承認（Phase 3 OK） | 「.companyos/ を co-note-production に scaffolding して」 |
| × 不十分な指示（Phase 3 NG） | 「続きを進めて」 |
| × 不十分な指示（Phase 3 NG） | 「次の作業をして」 |
| × 不十分な指示（Phase 3 NG） | 「進めてください」 |
| × 不十分な指示（Phase 3 NG） | 「OK」「了解」「お願いします」 |
| × 不十分な指示（Phase 3 NG） | 「先に進めて」「やって」 |
| × 不十分な指示（Phase 3 NG） | 「Step 0.5 だけやって」など部分指示 |

### 不十分な指示しかない場合の AI の行動

V4 (this repo) 内のレビュー / 設計更新 / feedback 整理 / その他 V4 内部作業に留める。

**target repo を勝手に編集する事故より、V4 内で何もしない方が圧倒的に安全**。

### AI が判断に迷ったら

迷ったら **V4 内に留まる方を選ぶ**。

それでも確認が必要な場合は、ユーザーに以下のように聞く：

> 「これは V4 内部の作業ですか？それとも co-note-production へ Phase 3 を適用する作業ですか？」

### 関連 gate

- `../../../CLAUDE.md` Absolute Rule 9 — V4 原則レベルの最初のゲート
- `../../../CLAUDE.gate.md` Stop Conditions の **「Phase 3 target repo application is being started without explicit user approval」** — V4 完了前検査
- このセクション — handoff レベルの正本（最も詳細）
- `../README.md` の AI への絶対ルール — pilot folder 入口

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

> **重要**: 冒頭の「Phase 3 実行条件」を満たすユーザー明示承認が出た**後**に、以下を実行する。
> 本 pilot 設計の Phase 3 適用は、V4 とは**別の作業セッション / 別の repo (`co-note-production`)** で実施する。
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

### Step 0.5: target repo 実体観察

> **Phase 3 安全弁。Step 1 以降に進む前に必ず実行する。**

`co-note-production` 側の実構造が V4 設計の前提と一致するかを確認する。
**存在しない物を勝手に作らない / 既存構造を勝手に変えない** ことが本 Step の唯一の目的。

V4 設計（`03_ssot_map.md` / `04_directory_design.md`）は `co-note-production` の特定構造を前提にしているが、これは V4 側の想定であり、target repo 側の実体と必ずしも一致しない。Phase 3 で AI / 人間が勝手に「足りないもの」を補完すると、archetype 適用が target 既存構造を破壊するリスクがある。

#### 実体観察 checklist（`co-note-production` で `ls` / `cat` / `grep` で確認）

**Group A: archetype 適用前提（reviewer 必須）** — このグループに欠落があれば Step 1 へ進む前に判定表を参照

| # | 確認項目 | 期待 |
| --- | --- | --- |
| A1 | `SPOKE.yml` の既存構造（**top-level key 一覧と値を記録**） | 既存 spoke 接続が動いている |
| A2 | `20_workspace/articles/` directory | 既存 |
| A3 | `20_workspace/articles/{slug}/meta.md` 構造例（1 件以上、key 一覧を記録） | 既存 |
| A4 | `02_workflows/note_article_production.md` | 既存 |
| A5 | `99_publish_history/` | 既存 |
| A6 | `30_feedback/raw/` | 既存 |
| A7 | `.companyos/` | **未存在** |

**Group B: 参考観察（必須ではない / 欠落しても Phase 3 を止めない）**

| # | 確認項目 | 期待 | 欠落時 |
| --- | --- | --- | --- |
| B1 | `README.md` | 既存 | 既存 README の有無確認のみ、欠落で停止しない |
| B2 | `10_assets/` | 既存 | 無くても note 制作は可能 |
| B3 | `31_learning/` | 既存 | 欠落していたら 30_feedback/raw に記録、Phase 3 は継続 |
| B4 | `90_archive/` | 既存 | 同上 |

Group A の欠落は **Phase 3 scope 再確認の対象**、Group B の欠落は **観測 append のみ**。

#### 観察結果の判定

| 結果 | 取る行動 |
| --- | --- |
| Group A 7 件すべて期待どおり、Group B も大半揃う | そのまま Step 1 へ進む |
| **Group A** の一部が欠けている | **勝手に作らない**。`co-note-production/30_feedback/raw/{YYYY-MM}.md` に「不足観測」として append。**saku に scope 調整を確認してから** Step 1 へ |
| **Group B** の一部が欠けている | 観測 append のみ。Step 1 へ進んでよい |
| `.companyos/` が **既に存在** | **Step 1 以降を実行しない**。既存 `.companyos/` を `tree` / `ls -la` で記録（後段判断に必要）。上書き前に saku 確認、merge / 共存方針を決める |
| 既存 `SPOKE.yml` の top-level key が V4 追加 block と衝突しそう（`archetype:` や `mvp_modules:` がすでに別意味で使われている等） | Step 4 で **`harness_designer_v4:` block 化方式** を採用することを事前に決定。後述の Step 4 補強を参照 |

#### 観察結果の記録（必須）

実体観察の結果は **必ず記録**する：

```text
co-note-production/30_feedback/raw/{YYYY-MM}.md に append:

### YYYY-MM-DD HH:MM — Phase 3 preflight 観測

- Group A（必須）N/7 件 期待どおり
- Group A 欠落: [列挙]
- Group B（参考）N/4 件 期待どおり
- 既存 `.companyos/` の有無: yes / no
  - yes の場合の中身（`tree` 出力 / `ls -la` 結果を貼り付け）
- 既存 SPOKE.yml top-level key 一覧（Step 4 検証で照合する）:
  - [key1, key2, ...]
- 衝突する V4 追加 key: なし / あり（詳細）
- 次のアクション: Step 1 へ進む / 一旦停止して saku 確認
- 関連 file: ...
```

> **重要**: 「既存 SPOKE.yml top-level key 一覧」は Step 4 で「既存値が変わっていないか」を `git diff` 検証する際の **照合元** になる。必ず記録しておく。

#### 失敗時の絶対ルール

- 不足 entry を **勝手に補完しない**（archetype 適用は existing repo の構造尊重が前提）
- `co-note-production` の既存 root を **勝手に変更しない**
- `.companyos/` が既存なら **絶対に上書きしない**
- Phase 3 scope を AI が独断で拡大しない
- 観測のみ記録 → saku 判断を待つ

### Step 1: 新ブランチ作成

```text
git checkout main
git pull origin main
git checkout -b feat/companyos-interface-scaffold
```

### Step 2: `.companyos/` 雛形を copy

V4 の `06_build/scaffolds/companyos_interface/` を `co-note-production/.companyos/` にコピーする。

> **環境前提**: 以下のコマンドは `co-harness-designer-v4` と `co-note-production` が **同一親 directory に sibling として存在する** ことを前提とする（例: 両方とも `/Users/saku/` 直下）。パスは実環境に合わせて調整すること。

#### 2-0: copy 前の dry-run / tree 確認（必須）

cp コマンドを叩く前に、コピー元の中身とコピー先の不在を **両方確認** する：

```text
# コピー元の中身を確認（雛形 file が全て存在するか）
ls -la co-harness-designer-v4/06_build/scaffolds/companyos_interface/
find co-harness-designer-v4/06_build/scaffolds/companyos_interface/ -type f

# コピー先が未存在であることを再確認（Step 0.5 で確認済みでも再 check）
test ! -e co-note-production/.companyos && echo "OK: copy 先未存在" || echo "STOP: copy 先既存"
```

`.companyos/` が **既に存在する**場合は cp を**実行しない**。Step 0.5 の判定に戻る（既存上書きは禁止）。

#### 2-1: 実 copy

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

### Step 4: `co-note-production/SPOKE.yml` を更新（block 化方式）

**既存 SPOKE.yml の構造を尊重する。同名 key の上書きは禁止**。V4 追加分は **専用 block `harness_designer_v4:` 配下にまとめて append** する。

#### 方針

- 既存の `spoke_id`, `version`, `connection`, `capabilities` 等は **触らない**
- V4 archetype 宣言は **`harness_designer_v4:` block 配下にまとめる**
- これにより、target repo 側の既存 SPOKE 構造を破壊せず、V4 追加分が grep / diff で識別しやすくなる
- 将来 V4 適用を削除する場合も、この block を消すだけで済む

#### 既存 SPOKE.yml の末尾に append する内容

```yaml
# V4 archetype 適用（Phase 3 で追加）
# 削除する場合はこの block ごと削除すれば原状復帰
harness_designer_v4:
  archetype: archetype.note_production_repo.v1
  applied_at: "{YYYY-MM-DD}"
  mvp_modules:
    - content_production
    - publish_pipeline
    - feedback_loop
  forbidden_modules:
    - client_ops
```

#### 既存 SPOKE.yml に同名 key がある場合

| 既存状態 | 取る行動 |
| --- | --- |
| 既存 SPOKE に `archetype:` top-level key が既にある | **上書きしない**。`harness_designer_v4.archetype` として block 内に書く。既存値は note としても残す |
| 既存 SPOKE に `mvp_modules:` top-level key が既にある | **上書きしない**。`harness_designer_v4.mvp_modules` として block 内に書く |
| 既存 SPOKE に `harness_designer_v4:` block が既に存在 | **編集前に saku 確認**。複数回適用 / 別 archetype 重複の可能性。Step 0.5 の判定に戻る |

#### 検証

`git diff SPOKE.yml` で以下を必ず確認：

- 既存項目に変更がない（既存 key の値が変わっていない）
  - **Step 0.5 の観察記録に保存した「既存 SPOKE.yml top-level key 一覧」と照合**
  - diff で既存 key の値が変わっていれば即座に revert
- 末尾に `harness_designer_v4:` block が追加されている
- archetype / mvp_modules / forbidden_modules の値が手順どおり
- `applied_at` 日付が実適用日

#### 検証 fail 時の手順

| diff 観察結果 | 取る行動 |
| --- | --- |
| 既存 key の値が変化 | 即 revert（`git checkout SPOKE.yml`）、saku に報告 |
| `harness_designer_v4:` block が無い | append し直し |
| block 内の値が手順と異なる | 修正、再 diff 確認 |
| `applied_at` が空 / 過去日 | 実適用日に修正 |

### Step 5: Critical Gates 自己 check（短縮チェック）

> **重要**: 以下は **短縮チェック**であり、正式な合格判定の正本は：
> - `../07_quality_plan.md` の **acceptance criteria 10/10**（本 pilot 専用の合格基準）
> - `../../../07_quality/30_critical_gates.md` の **全 critical gates** （V4 共通正本）
>
> 短縮チェックだけで合格判定しないこと。両正本との照合が完了して初めて Step 6 へ進む。

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
### YYYY-MM-DD HH:MM — V4 archetype 適用: note_production_repo

- V4 `06_build/scaffolds/companyos_interface/` を `.companyos/` にコピー適用
- 3 surface + sync + generated の雛形を実 source_pin で埋めた
- 業務正本は通常 dir のまま（コピーゼロ）
- MNP block は書かなかった（installed/ 昇格前）
- SPOKE.yml は `harness_designer_v4:` block を末尾に append（既存 top-level key は無変更、Step 0.5 記録と照合済み）
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
### YYYY-MM-DD HH:MM — Phase 3 完了: co-note-production への .companyos 適用

- Step 0.5 preflight: Group A N/7, Group B N/4 の観察結果
- Step 1-7 が完走したか / どこで詰まったか
- 雛形 → 実 source_pin 変換で迷ったポイント
- scaffold が `co-note-production` の既存 root と摩擦したか
- Step 4 SPOKE.yml block 追記: 既存 key 無変更で完了したか
- 次の archetype (client_repo) 適用前に直したい点
- 関連 file: `co-note-production/.companyos/`（全 10）, SPOKE.yml
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
