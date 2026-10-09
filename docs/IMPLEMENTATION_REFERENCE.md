# 応募者管理画面 実装連携ガイド

## 目的

応募者管理画面を、バックエンド担当へ渡しやすい静的HTMLモックとして作成するための基準をまとめる。

見た目だけの専用構造を避け、本番実装へ移行しやすいHTMLとSassで構成する。

## 資料の優先順位

1. `SPEC.md`
2. `DESIGN_TOKENS.md`
3. `BACKEND_HANDOFF.md`
4. `LAYOUT_TEMPLATE.md`
5. `IMPLEMENTATION_REFERENCE.md`

## 基本方針

- 静的HTMLモックとしてデザインする
- 用途に合うHTML要素を使用する
- 見た目のためだけにフォーム要素を `div` や `span` へ置き換えない
- PHP、API、DB連携は実装しない
- JavaScriptは表示・操作確認に必要な最小限にする
- ReactやNext.jsなど、指定されていない環境へ変更しない
- 不要な抽象化や過剰な共通化を行わない

## 作成対象

- `index.html`：管理画面ログイン
- `applicants.html`：応募者一覧
- `applicant-detail.html`：応募者詳細

## HTML構成

### 共通

- 共通ヘッダー：`.container-header`
- ヘッダー下の全体レイアウト：`.inner-body`
- 左メニュー：`.block-sidebar`
- ページの主要内容：`main`
- ページ見出し：`.page-header`
- 状態違い：`.is-active`、`.is-current`、`.is-empty`、`.is-error`
- JavaScriptの操作対象：必要に応じて `id`、`data-*`、`aria-*` を付ける

### 応募者一覧

- 検索・絞り込みは `form` で囲む
- 入力項目には `label` を関連付ける
- 一覧は `table` を使用する
- 列見出しは `th`、データセルは `td` を使用する
- 詳細画面への遷移は `a` を使用する
- ページネーションは `nav` を使用し、`aria-label` を付ける

### 応募者詳細

- 応募フォームのStep 1〜4に対応する単位で `section` を分ける
- 項目名と値の関係が分かる `dl`、`dt`、`dd` を基本にする
- 職務経歴書へのリンクは `a` を使用する
- 一覧へ戻る操作は `a` を使用する

## Sass構成

```text
assets/
├── scss/
│   ├── foundation/
│   │   ├── _index.scss
│   │   ├── _settings.scss
│   │   ├── _colors.scss
│   │   ├── _breakpoints.scss
│   │   ├── _typography.scss
│   │   ├── _interaction.scss
│   │   ├── _ui.scss
│   │   └── _reset.scss
│   ├── globals.scss
│   ├── login.scss
│   ├── applicants.scss
│   └── applicant-detail.scss
└── css/
    ├── globals.css
    ├── login.css
    ├── applicants.css
    └── applicant-detail.css
```

### 分割ルール

- `foundation/`：変数、関数、mixin、リセット
- `foundation/_index.scss`：ページ別Sassから参照する共通入口
- `globals.scss`：body、ヘッダー、サイドバー、共通フォーム、共通ボタン
- `login.scss`：ログインカード、認証エラー、ログインフォーム
- `applicants.scss`：集計カード、検索、テーブル、ページネーション
- `applicant-detail.scss`：応募者概要、情報セクション、項目リスト
- ページ別Sassでは `@use "./foundation/" as *;` を基本にする

## CSSの読み込み

応募者一覧：

```html
<link rel="stylesheet" href="assets/css/globals.css">
<link rel="stylesheet" href="assets/css/applicants.css">
```

応募者詳細：

```html
<link rel="stylesheet" href="assets/css/globals.css">
<link rel="stylesheet" href="assets/css/applicant-detail.css">
```

## Sassコマンド

`package.json` では次のスクリプト名を使用する。

```json
{
  "scripts": {
    "sass": "sass assets/scss:assets/css",
    "watch:sass": "sass --watch assets/scss:assets/css",
    "sass:prod": "sass assets/scss:assets/css --style=compressed --no-source-map"
  }
}
```

`node_modules` は参照元からコピーせず、`package.json` と `package-lock.json` から再現する。

## 完了時の確認

- 一覧と詳細の画面遷移ができるか
- 応募フォームと管理画面の項目が一致しているか
- テーブルと詳細情報の構造が意味的に適切か
- 共通スタイルとページ固有スタイルが分かれているか
- PCの基準幅と縮小時の表示をブラウザで確認したか
- 横スクロールが必要な箇所の扱いが明確か
- 仮データと確定仕様が混同されていないか
- 不要な装飾用タグや未使用classが残っていないか
