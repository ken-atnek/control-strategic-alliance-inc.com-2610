# 応募者管理画面 共通レイアウトテンプレート

## 位置づけ

HTMLモックを実装に近い構造で作成するためのテンプレート。

画面項目は `SPEC.md`、デザインは `DESIGN_TOKENS.md`、実装方針は `IMPLEMENTATION_REFERENCE.md` を参照する。

## ログイン

```html
<body class="admin-page login-page">
  <main class="login">
    <div class="login__card">
      <div class="login__brand">
        <img src="assets/images/logo.png" alt="STRATEGIC ALLIANCE inc.">
        <span>採用管理</span>
      </div>

      <h1 class="login__title">ログイン</h1>

      <p class="login__error is-error" role="alert">
        メールアドレスまたはパスワードが正しくありません。
      </p>

      <form class="login__form" action="" method="post">
        <!-- メールアドレス / パスワード / ログイン状態保持 -->
        <button type="submit" class="btn btn--primary login__submit">ログイン</button>
      </form>
    </div>
  </main>
</body>
```

## 応募者一覧

```html
<body class="admin-page applicants-page">
  <header class="container-header">
    <a class="admin-brand" href="applicants.html">
      <img src="assets/images/logo.png" alt="STRATEGIC ALLIANCE inc.">
      <span>採用管理</span>
    </a>
  </header>

  <div class="inner-body">
    <aside class="block-sidebar">
      <nav aria-label="管理メニュー">
        <a class="is-current" href="applicants.html">応募者管理</a>
      </nav>
    </aside>

    <main>
      <div class="page-header">
        <div>
          <p class="page-header__eyebrow">Applicants</p>
          <h1>応募者一覧</h1>
        </div>
      </div>

      <section class="summary" aria-label="応募者数">
        <!-- 応募者総数 / 期間内の応募者数 -->
      </section>

      <form class="applicant-search" action="" method="get">
        <!-- キーワード / 応募日 / 就業状況 / 経験年数 -->
      </form>

      <section class="applicant-list" aria-labelledby="applicant-list-title">
        <h2 id="applicant-list-title">応募者</h2>
        <div class="table-scroll">
          <table>
            <!-- thead / tbody -->
          </table>
        </div>
        <nav class="pagination" aria-label="応募者一覧のページ送り">
          <!-- ページネーション -->
        </nav>
      </section>
    </main>
  </div>
</body>
```

## 応募者詳細

```html
<body class="admin-page applicant-detail-page">
  <header class="container-header">
    <a class="admin-brand" href="applicants.html">
      <img src="assets/images/logo.png" alt="STRATEGIC ALLIANCE inc.">
      <span>採用管理</span>
    </a>
  </header>

  <div class="inner-body">
    <aside class="block-sidebar">
      <nav aria-label="管理メニュー">
        <a class="is-current" href="applicants.html">応募者管理</a>
      </nav>
    </aside>

    <main>
      <a class="back-link" href="applicants.html">応募者一覧へ戻る</a>

      <div class="page-header">
        <div>
          <p class="page-header__eyebrow">Applicant details</p>
          <h1>応募者詳細</h1>
        </div>
      </div>

      <div class="applicant-summary">
        <!-- 氏名 / 応募日時 -->
      </div>

      <div class="applicant-detail">
        <section class="detail-section" aria-labelledby="basic-info-title">
          <h2 id="basic-info-title">基本情報</h2>
          <dl><!-- Step 1の項目 --></dl>
        </section>

        <section class="detail-section" aria-labelledby="experience-title">
          <h2 id="experience-title">経験・スキル</h2>
          <dl><!-- Step 2の項目 --></dl>
        </section>

        <section class="detail-section" aria-labelledby="career-title">
          <h2 id="career-title">保有資格・職務経歴</h2>
          <dl><!-- Step 3の項目 --></dl>
        </section>

        <section class="detail-section" aria-labelledby="free-input-title">
          <h2 id="free-input-title">自由入力</h2>
          <dl><!-- Step 4の項目 --></dl>
        </section>
      </div>
    </main>
  </div>
</body>
```

## 注意

- 実際の検索、ページ移動、DB連携は実装しない
- フォーム、リンク、テーブルは用途に合うHTML要素を使用する
- 詳細画面の分類・項目名・並び順は `SPEC.md` に合わせる
- 共通スタイルとページ固有スタイルを分ける
- class名はバックエンド実装で用途が読み取れる名前を保つ
- `data-href` だけに依存せず、詳細ページへの `a` を必ず設置する
