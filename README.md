# STRATEGIC ALLIANCE 応募者管理画面

## 概要

株式会社ストラテジックアライアンスの応募者情報を確認する、バックエンド引き渡し用の静的HTMLモックプロジェクト。

完成済みの管理画面デザインを本作業ディレクトリへ移し、バックエンド担当が実装へ接続しやすいHTML/Sass構成に整理する。

## 対象画面

- `login.html`：管理画面ログイン
- `applicants.html`：応募者一覧
- `applicant-detail.html`：応募者詳細

独立したダッシュボード、ユーザー管理、各種設定画面は作成しない。

## 参照ドキュメント

- `docs/README.md`：ドキュメント一覧と参照元
- `docs/SPEC.md`：画面・機能仕様
- `docs/DESIGN_TOKENS.md`：カラー・UIルール
- `docs/LAYOUT_TEMPLATE.md`：HTML構造の目安
- `docs/IMPLEMENTATION_REFERENCE.md`：HTML・Sass構成
- `docs/BACKEND_HANDOFF.md`：バックエンド引き渡し時の確認事項
- `docs/PROJECT_STATUS.md`：現在地と次の作業

## 基本方針

- 静的HTML/Sassで作成する
- 採用サイトと同じネイビー、ゴールドを使用する
- 装飾より、一覧性・検索性・情報の確認しやすさを優先する
- 検索、ページネーション、詳細表示はバックエンド接続前のモックとして表現する
- PHP、API、DB、認証処理は実装しない
- 未確定機能は追加しない

## Sass

```bash
npm install
npm run sass
npm run watch:sass
npm run sass:prod
```

Sassは次の構成で管理する。

```text
assets/scss/
├── foundation/
├── globals.scss
├── login.scss
├── applicants.scss
└── applicant-detail.scss
```

コンパイル後のCSSは `assets/css/` に出力する。

## DDEV

```bash
ddev start
ddev npm install
ddev npm run sass
```

ローカルURL：

```text
https://control-strategic-2610.ddev.site
```

## 参照元

- デザイン・案件仕様：`/Users/ken/site_data/__web_design/ストラテジックアライアンス`
- 管理画面構成の参考：`/Users/ken/site_data/1016design/control.yamagarotenyu-momiji.com`

参照元のファイルは直接編集せず、本プロジェクト内で作業する。
