# 饗応元 公式サイト（SEO/MEO対応版）— セットアップ手順

このフォルダには、饗応元（キョウオウハジメ）の新しい公式サイト一式が入っています。
すべて無料ツールだけで公開できるように作ってあります。ここに書いてある順番通りに進めてください。

## 中身

```
index.html      … トップページ
menu.html       … メニュー
about.html      … 店主のこだわり
access.html     … アクセス・店舗情報
news.html       … お知らせ
404.html        … ページが見つからない時に表示されるページ
css/style.css   … デザイン
js/main.js      … スマホ用メニューの開閉だけの軽いスクリプト
images/         … 画像フォルダ（下記の手順で写真を追加してください）
sitemap.xml     … Googleにページ一覧を伝えるファイル
robots.txt      … クロール許可の設定ファイル
```

## 前回の反省点（重要）

以前のサイト（kyouou-hajime.vercel.app）は、作った人以外がログイン情報を把握していない状態でした。
今回は **必ずハルキさん自身のアカウントで** 公開してください。そうすれば今後は誰でも自由に更新・引き継ぎができます。

---

## 手順1：写真を用意する

このフォルダの `images/` には favicon（サイトアイコン）しか入っていません。
以前のサイトで使われていた4枚の写真は、ログインしなくても以下のURLから直接保存できます（右クリック→「名前を付けて画像を保存」）。

- https://kyouou-hajime.vercel.app/exterior.jpg → `images/exterior.jpg` として保存
- https://kyouou-hajime.vercel.app/interior.jpg → `images/interior.jpg` として保存
- https://kyouou-hajime.vercel.app/meat.jpg → `images/meat.jpg` として保存
- https://kyouou-hajime.vercel.app/sake_collection.jpg → `images/sake_collection.jpg` として保存

同じファイル名で `images/` フォルダに入れれば、そのまま表示されます。
もちろん、お店の最新の写真に差し替えていただいても構いません（ファイル名は同じにするのが一番簡単です）。

## 手順2：メニュー内容を実際のものに更新する

`menu.html` は構成だけ作ってあり、具体的な料理名・価格は入れていません（正確な情報が分からなかったため）。
以前作成された日本酒リストやドリンクメニューの内容を参考に、`menu.html` 内の「料理のこだわり」「日本酒・お酒」の部分を実際のお品書きに書き換えることをおすすめします。ここは私（Claude）に「このメニュー内容で書き換えて」と頼んでいただければ、いつでも反映できます。

## 手順3：無料で公開する（GitHub Pages）

一番おすすめなのは **GitHub Pages**（完全無料・独自ドメインも設定可）です。

1. https://github.com にアクセスし、**ハルキさん自身の**アカウントを作成（無料）
2. 右上の「+」→「New repository」で新しいリポジトリを作成
   - Repository name: `kyouou-hajime`（何でも可）
   - Public を選択
3. 作成後、「uploading an existing file」からこのフォルダの中身（index.html や css フォルダなど）を **フォルダごと** ドラッグ&ドロップしてアップロード
4. リポジトリの Settings → Pages → Source を「Deploy from a branch」、Branch を「main」に設定して Save
5. 数分後、`https://（アカウント名）.github.io/kyouou-hajime/` でサイトが公開されます

### 独自ドメインを使いたい場合

お名前.com やGoogle Domainsなどで独自ドメイン（例: kyouou-hajime.jp）を取得し、GitHub Pagesの「Custom domain」欄に設定すると、そのドメインで公開できます（ドメイン自体は有料ですが、ホスティングは無料のままです）。

## 手順4：ドメイン名を実際のものに置き換える

このサイトのファイル内では仮のドメインとして `https://kyouou-hajime.jp` を使っています。
実際に使うURL（例: `https://ハルキさんのアカウント.github.io/kyouou-hajime` や取得した独自ドメイン）が決まったら、以下のファイル内の `https://kyouou-hajime.jp` をすべて実際のURLに置き換えてください。

- `index.html`, `menu.html`, `about.html`, `access.html`, `news.html`（canonical・OGP・構造化データ部分）
- `sitemap.xml`
- `robots.txt`

置き換えは私に「ドメインが〇〇に決まったので置き換えて」と伝えていただければ、まとめて対応します。

## 手順5：Google Search Consoleに登録する（無料・SEOの基本）

1. https://search.google.com/search-console にアクセスし、Googleアカウントでログイン
2. 「プロパティを追加」→ 公開したサイトのURLを入力
3. 所有権の確認（HTMLファイルのアップロード or DNS認証など、画面の指示に従う）
4. 確認後、「サイトマップ」メニューから `sitemap.xml` を送信

これでGoogleにページの存在を正しく伝えられ、インデックス登録が早まります。

## 手順6：Googleビジネスプロフィール（MEO）との整合性を保つ

Googleビジネスプロフィールはすでに運用されているとのことですので、新しいサイトと**表記を完全に一致させる**ことがMEO（地図・ローカル検索対策）で最も重要です。

- 店名・住所・電話番号（NAP情報）をGoogleビジネスプロフィールと1文字も違わないように揃える
- Googleビジネスプロフィールの「ウェブサイト」欄を新しいサイトのURLに更新する
- 水曜ランチ（11:45〜13:45）の情報は、TripAdvisor・食べログにも反映が必要（メモリに記録済みの未対応事項）

## 更新方法（お知らせページ）

`news.html` 内のコメントに沿って、`<article class="news-item">...</article>` のブロックをコピーして一番上に追加すれば新しいお知らせを追加できます。定期的に更新するとGoogleに「動いているサイト」と認識されやすくなります（SEOのプラス要素）。

## 今回のSEO/MEO対策のポイント（サマリー）

- 構造化データ（JSON-LD）でRestaurant情報・パンくずリストをGoogleに正しく伝達
- ページごとに固有のtitle・meta description・OGP設定
- 意味のある見出し構造（h1〜h3）とセマンティックHTML
- サイトマップ・robots.txtでクロールを最適化
- モバイル対応・軽量な作り（画像はloading="lazy"、余分なJS・外部ライブラリなし）
- Googleマップの埋め込み（APIキー不要の無料方式）
- 内部リンクでページ同士を接続（トップ→メニュー/アクセス/こだわり）
- お知らせページで更新頻度（鮮度シグナル）を確保

## まだ手を付けていないこと（今後の相談ポイント）

- 実際のメニュー内容・価格の反映
- 独自ドメインの取得・設定（希望があれば）
- Google Analytics（無料のアクセス解析）の導入
- TripAdvisor・食べログの水曜ランチ情報の修正（別件で進行中）
