# AGENTS.md

## プロジェクト概要

株式会社ストラテジックアライアンスの採用管理画面を、バックエンド実装へ渡すための静的HTMLモックとして構築する。

- 対象はログイン、応募者一覧、応募者詳細
- 採用サイトのブランドトーンを引き継ぐ
- 画面構造・フォーム項目・状態・導線を、バックエンド担当が読み取りやすい構成にする
- 実ログイン、検索、保存、API、DB連携は実装しない

## 作業前の参照順

1. `README.md`
2. `docs/README.md`
3. `docs/SPEC.md`
4. `docs/DESIGN_TOKENS.md`
5. `docs/LAYOUT_TEMPLATE.md`
6. `docs/IMPLEMENTATION_REFERENCE.md`
7. `docs/BACKEND_HANDOFF.md`
8. `docs/PROJECT_STATUS.md`

## 参照プロジェクト

### 画面デザイン・案件仕様

`/Users/ken/site_data/__web_design/ストラテジックアライアンス`

- 応募者管理画面のHTMLモックとSass
- 応募フォームの項目
- ブランドカラーとUIトーン

### 管理画面の実装構成

`/Users/ken/site_data/1016design/control.yamagarotenyu-momiji.com`

- 静的HTMLモックのまとめ方
- Sass、DDEV、バックエンド引き渡し資料の構成
- 案件固有の空室管理仕様や色、文言は流用しない

## 実装ルール

- 既存仕様を優先し、大幅な設計変更を行わない
- まず静的HTML/CSSとして整える
- HTMLは用途に合う `form`、`input`、`select`、`button`、`label`、`table`、`dl` を使用する
- JavaScriptは表示・操作確認に必要な最小限にする
- React、Next.jsなど別環境へ変更しない
- Sass入口はページごとに分け、共通スタイルは `globals.scss` に置く
- デザイントークンは `docs/DESIGN_TOKENS.md` を正とする
- 実装難易度を理由にデザインを簡略化しない

## ローカル環境

- DDEVプロジェクト名は `control-strategic-2610`
- DDEVのdocrootはプロジェクト直下
- PHP 8.4、Apache FPM、MariaDB 11.8、Node.js 24を使用する
- Sass確認は `ddev npm run sass` を基本にする
- DDEVを使わない簡易確認では `npm run sass` を使用してよい
- `node_modules` はコピーせず、`npm install` で再生成する

## 変更時の注意

- 修正箇所を明確にする
- 一度に大量変更しない
- 既存ファイルを確認してから編集する
- class名、id属性、name属性など、バックエンド連携に関わる変更は特に慎重に行う
- 未確定事項を推測で確定しない
