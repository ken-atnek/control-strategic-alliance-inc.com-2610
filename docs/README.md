# ドキュメント一覧

最終更新：2026-10-09

## 現在参照する資料

| ファイル | 役割 |
| --- | --- |
| `../AGENTS.md` | プロジェクト固有の作業ルールと参照順 |
| `../README.md` | プロジェクト概要 |
| `SPEC.md` | 応募者一覧・詳細画面の確定仕様 |
| `DESIGN_TOKENS.md` | ブランドカラーとUIルール |
| `LAYOUT_TEMPLATE.md` | 一覧・詳細のHTML構造テンプレート |
| `IMPLEMENTATION_REFERENCE.md` | HTML・Sassの実装方針 |
| `BACKEND_HANDOFF.md` | バックエンド接続時の確認事項 |
| `PROJECT_STATUS.md` | 現在地、未確定事項、次の作業 |

## 取り込み元

### 案件固有の仕様・デザイン

`/Users/ken/site_data/__web_design/ストラテジックアライアンス`

- `docs/APPLICANT_ADMIN_SPEC.md`
- `docs/DESIGN_TOKENS.md`
- `docs/coding/LAYOUT_TEMPLATE.md`
- `docs/coding/IMPLEMENTATION_REFERENCE.md`
- `applicants.html`
- `applicant-detail.html`
- `login.html`

### 管理画面プロジェクトの構成参考

`/Users/ken/site_data/1016design/control.yamagarotenyu-momiji.com`

- `AGENTS.md`
- `README.md`
- `docs/BACKEND_HANDOFF.md`
- `docs/MEMORY.md`

## 取り込まない資料

- 山鹿管理画面固有の空室管理仕様、状態値、色、文言
- `CLAUDE_REVIEW.md`、`CLAUDE_REVIEW_02.md`：別案件のレビュー記録
- デザイン元の `docs/archive/`：採用サイト制作時の履歴
- デザイン元の `RECRUIT_SITE_SPEC.md`：採用サイト全体の仕様。管理画面で必要な応募項目は `SPEC.md` に集約
- `CLAUDE.md`：`AGENTS.md` と本ドキュメントへ必要事項を統合

## 優先順位

仕様が食い違う場合は、次の順で判断する。

1. `SPEC.md`
2. `DESIGN_TOKENS.md`
3. `BACKEND_HANDOFF.md`
4. `LAYOUT_TEMPLATE.md`
5. `IMPLEMENTATION_REFERENCE.md`
