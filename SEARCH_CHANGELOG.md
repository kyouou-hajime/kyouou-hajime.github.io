# 饗応 元｜検索対策・HP変更履歴

日付は日本時間。原稿完成・GitHub反映・公開ページ確認・検索側の再取得を区別する。
各変更の差分は記載のコミットとGitHub履歴で確認できる。順位上昇・AI引用は保証しない。
安全な修正はユーザーの包括的な許可（2026-10-07）に基づいて実施する。料金・未確認情報・外部アカウント設定などは推測で変更しない。


## 2026-10-10

### トップページで「酒匠」と「唎酒師」の関係を明示
- 対象：index.html の酒匠紹介本文。
- 変更前：「日本酒・焼酎のテイスティングと提案に関する上位資格。」
- 変更後：「唎酒師・焼酎唎酒師の上位資格『酒匠』。」
- 理由：知名度の高い「唎酒師」から専門資格の位置づけをすぐ理解できるようにする。資格説明の詳細は既存の sakasho.html と一致。
- コミット：4ae8fe9024192808e20717438cada09df17e5edb
- 確認：GitHubの保存内容を再取得。2026-10-10に公開トップをブラウザで確認し、「唎酒師・焼酎唎酒師の上位資格『酒匠』。」の反映、既存の料理・予約導線、営業時間、構造化データ表示の維持を確認。
- 状態：公開反映確認済み。検索側の再取得・表示、AI引用は未確認。

## 2026-10-08

### 「丸太町と日本酒」ページをRestaurant・WebSite実体へ接続（公開ページ反映確認済み）
- 対象：marutamachi-sake.html、sitemap.xml。
- 修正前：構造化データはBreadcrumbListのみで、この地域・日本酒案内ページと、トップページのRestaurant実体・公式WebSiteとの関係が未定義。
- 修正後：WebPage構造化データを追加し、ページ固有@id、正規URL、既存title/description、言語を設定。about・mainEntity・publisherでRestaurant共通@id、isPartOfでWebSite共通@idへ接続。sitemap.xmlのmarutamachi-sake.htmlのlastmodを2026-10-08へ更新。
- 理由：丸太町で日本酒を楽しむ利用場面を説明する既存ページが、饗応 元の公式案内であることを検索エンジン・AIへ機械可読で示すため。
- 根拠：Schema.orgはWebPageをWebページ用の型とし、aboutを対象の主題、mainEntityをページで説明される主要実体、isPartOfを所属するCreativeWorkとして定義している。
  - https://schema.org/WebPage
  - https://schema.org/mainEntity
  - https://schema.org/isPartOf
- 変更していないもの：画面本文、見出し、料理、日本酒、価格、営業時間、予約条件、予約URL、画像。
- コミット：
  - marutamachi-sake.html：06784e5ce71191ca99b2ba00dbf24716adad60e2
  - sitemap.xml：2691538ad41bddf24174ea29ffdd2264785cbb83
- 検証：GitHub保存内容を再取得し、BreadcrumbList・WebPageの全JSON構文解析成功、Restaurant/WebSite共通@id、sitemap更新を確認。GitHub Pagesのデプロイ成功後、2026-10-08に公開marutamachi-sake.htmlを再取得し、WebPage固有@idとRestaurant/WebSite共通@idの反映を確認。公開sitemap.xmlは確認環境のクライアント制限で直接再取得できず、GitHub保存内容とデプロイ成功まで確認。
- 状態：公開ページ反映確認済み。sitemapはGitHub反映・デプロイ成功確認済み。
- 未解決：検索側の再取得・表示、AI引用は未確認。確認待ち質問の追加なし。

### 肉会FAQをRestaurant・WebSite実体へ接続（公開反映確認済み）
- 対象：nikukai.html、sitemap.xml。
- 点検：画面本文・meta description・FAQPageで、毎月29日、コース10,500円（ドリンク別）、2日前までの予約が一致。構造化データはBreadcrumbListとFAQPageのみ。
- 修正前：FAQPageは3件のQuestion/Answerのみで、ページ固有ID・正規URL・ページ名・説明・言語、店舗・公式サイト・発行元との関係が未定義。
- 修正後：既存FAQPageへページ固有@id、正規URL、既存title/description、言語を追加。about・publisherでRestaurant共通@id、isPartOfでWebSite共通@idへ接続。sitemap.xmlのnikukai.htmlのlastmodを2026-10-08へ更新。
- 理由：肉会の内容・料金・予約条件に関する3問が、饗応 元の公式案内であることを検索エンジン・AIへ機械可読で示すため。
- 根拠：Schema.orgはFAQPageを複数のよくある質問を提示するWebPageと定義し、継承するCreativeWorkのabout・isPartOf等を利用できるとしている。
  - https://schema.org/FAQPage
  - https://schema.org/about
  - https://schema.org/isPartOf
- 意図的に追加していないもの：単発Event。肉会は毎月29日の反復企画で、開催年月日を固定した単発イベントとして誤認させないため。
- 変更していないもの：画面本文、質問回答3件、価格、開催条件、営業時間、予約URL、画像。
- コミット：
  - nikukai.html：6135cbc5f9d9019ca991aec7905f15ee8957d033
  - sitemap.xml：c92f1d52c0b470c816829a4afd69792afc3580ae
- 検証：GitHub保存内容を再取得し、BreadcrumbList・FAQPageの全JSON構文解析成功、質問回答3件維持、Restaurant/WebSite共通@id、価格回答1件、sitemap更新を確認。GitHub Pagesのデプロイ成功後、2026-10-08に公開nikukai.htmlとsitemap.xmlを再取得して同内容を確認。
- 状態：公開反映確認済み。
- 未解決：検索側の再取得・表示、AI引用は未確認。確認待ち質問の追加なし。

### お知らせ一覧をCollectionPageとして店舗実体へ接続（公開反映確認済み）
- 対象：news.html、sitemap.xml。
- 修正前：お知らせページの構造化データはBreadcrumbListのみで、一覧ページ種別、店舗・公式サイト・発行元との関係が未定義。
- 修正後：CollectionPage構造化データを追加し、ページ固有@id、正規URL、既存title/description、言語を設定。about・publisherでRestaurant共通@id、isPartOfでWebSite共通@idへ接続。sitemap.xmlのnews.htmlのlastmodを2026-10-08へ更新。
- 理由：営業・イベント等のお知らせをまとめた公式一覧ページであり、発行主体が饗応 元であることを検索エンジン・AIへ機械可読で示すため。
- 根拠：Schema.orgはCollectionPageをコレクションページ用のWebPage型と定義し、継承するCreativeWorkのabout・isPartOf等を利用できるとしている。
  - https://schema.org/CollectionPage
  - https://schema.org/about
  - https://schema.org/isPartOf
- 意図的に追加していないもの：個別EventやOffer。開催条件・価格・営業予定の変化による構造化データの不一致を避けるため。
- 変更していないもの：画面本文、告知日、イベント内容、価格、営業時間、予約URL、画像。
- コミット：
  - news.html：de30959b15fe1d69e55790d62db4639b0690496a
  - sitemap.xml：48cee152e60810c37ad98dc40b4a534fd29c7bff
- 検証：GitHub保存内容を再取得し、BreadcrumbList・CollectionPageの全JSON構文解析成功、Restaurant/WebSite共通@id、sitemap更新を確認。GitHub Pagesのデプロイ成功後、2026-10-08に公開news.htmlとsitemap.xmlを再取得して同内容を確認。
- 状態：公開反映確認済み。
- 未解決：検索側の再取得・表示、AI引用は未確認。確認待ち質問の追加なし。

### 予約・営業FAQをRestaurant・WebSite実体へ接続（公開反映確認済み）
- 対象：faq.html、sitemap.xml。
- 修正前：FAQPageは11件のQuestion/Answerのみで、ページ固有ID・正規URL・ページ名・説明・言語と、公式店舗・サイトとの関係が未定義。
- 修正後：既存FAQPageへページ固有@id、正規URL、既存title/description、言語を追加。about・publisherでRestaurant共通@id、isPartOfでWebSite共通@idへ接続。sitemap.xmlのfaq.htmlのlastmodを2026-10-08へ更新。
- 理由：予約・営業時間・アクセス・料理・日本酒に関する11問が、饗応 元の公式FAQであることを検索エンジン・AIへ機械可読で示すため。
- 根拠：Schema.orgはFAQPageを複数のよくある質問を提示するWebPageと定義し、継承するCreativeWorkのaboutでページの主題、isPartOfで所属するCreativeWorkを示せるとしている。
  - https://schema.org/FAQPage
  - https://schema.org/about
  - https://schema.org/isPartOf
- 変更していないもの：表示中の質問・回答11件、営業時間、予約条件、料理、価格、リンク、本文。
- コミット：
  - faq.html：eeace768151ea8c16ba4a3db0e8a07b52ad94bdc
  - sitemap.xml：36afbdc02f0e653a7b32a93e0ec0428d0067038f
- 検証：GitHub保存内容を再取得し、BreadcrumbList・FAQPageの全JSON構文解析成功、質問回答11件維持、Restaurant/WebSite共通@id、sitemap更新を確認。GitHub Pagesのデプロイ成功後、2026-10-08に公開faq.htmlとsitemap.xmlを再取得して同内容を確認。
- 状態：公開反映確認済み。
- 未解決：検索側の再取得・表示、AI引用は未確認。FAQリッチリザルトを期待する施策ではない。確認待ち質問の追加なし。

### 料理・酒ページをRestaurant実体のMenuとして接続（公開反映確認済み）
- 対象：index.html、menu.html、sitemap.xml。
- 修正前：トップページのRestaurantは旧プロパティmenuで料理・酒ページのURLだけを指定。料理・酒ページの構造化データはBreadcrumbListのみで、店舗のメニュー実体との関係が未定義。
- 修正後：
  - Restaurantの旧menu指定を現行hasMenuへ置換し、料理・酒ページのMenu固有@idを参照。
  - menu.htmlへMenu構造化データを追加し、既存title/descriptionに基づく名称・説明・正規URL・言語を設定。
  - MenuをaboutでRestaurant共通@id、isPartOfでWebSite共通@idへ接続。
  - sitemap.xmlのトップとmenu.htmlのlastmodを2026-10-08へ更新。
- 理由：店舗と公式の料理・酒ページの関係を、URLだけでなく同一Menu実体として検索エンジン・AIへ明示するため。
- 根拠：Schema.orgはMenuを「FoodEstablishmentで提供される飲食物の構造化表現」、hasMenuをMenu・テキスト・URLで実際のメニューを示すFoodEstablishment用プロパティと定義し、旧menuをhasMenuが置き換えるとしている。
  - https://schema.org/Menu
  - https://schema.org/hasMenu
- 意図的に追加していないもの：日替わりの在庫・価格・個別MenuItem。表示内容との不一致を避けるため。
- 変更していないもの：画面本文、見出し、料理名、価格、営業時間、予約URL、画像。
- コミット：
  - index.html：d3fa2587695af6fb15a679653600f20f82e6113d
  - menu.html：44fa8343a5bb224d374d22a8f3a38af76fc70c3a
  - sitemap.xml：1e945f2c7f97e31429e424d4c0d4c5c02df67098
- 検証：GitHub保存内容を再取得し、全JSON-LD構文解析成功、RestaurantのhasMenuとMenuの@id完全一致、旧menu指定の除去、Restaurant/WebSite共通@id、sitemap更新を確認。GitHub Pagesのデプロイ成功後、2026-10-08に公開トップ・menu.html・sitemap.xmlを再取得して同内容を確認。
- 状態：公開反映確認済み。
- 未解決：検索側の再取得・表示、AI引用は未確認。確認待ち質問の追加なし。

### 「こだわり」ページを店舗実体へ接続（公開反映確認済み）
- 対象：about.html、sitemap.xml。
- 修正前：こだわりページの構造化データはBreadcrumbListのみで、ページ種別と、トップページのRestaurant実体との関係が未定義。
- 修正後：AboutPage構造化データを追加。ページ固有@id・正規URL・既存title/description・言語を設定し、about/mainEntityでトップページのRestaurant共通@id、isPartOfでWebSite共通@idへ接続。sitemap.xmlのabout.htmlのlastmodを2026-10-08へ更新。
- 理由：料理・食材・日本酒・店内について説明する既存ページが、饗応 元についての公式紹介ページであることを検索エンジン・AIへ機械可読で示すため。
- 根拠：Schema.orgはAboutPageを「About pageのWebページ型」と定義し、CreativeWorkのaboutを「対象の主題」、mainEntityを「ページ等で説明される主要な実体」と定義している。
  - https://schema.org/AboutPage
  - https://schema.org/about
  - https://schema.org/mainEntity
- 変更していないもの：画面本文、見出し、料理、価格、営業時間、予約URL、画像。
- コミット：
  - about.html：6f4e607f6c853276d179adc7d0b62edd5dce407a
  - sitemap.xml：4fac4c6701c1568ebeb09bd0e0b3e648bd0892fb
- 検証：GitHub保存内容を再取得し、BreadcrumbList・AboutPageの全JSON構文解析成功、AboutPageのabout/mainEntity/isPartOfがトップページの共通@idと一致、sitemap更新を確認。GitHub Pagesのデプロイ成功後、2026-10-08に公開about.htmlとsitemap.xmlを再取得し、AboutPage固有@id、Restaurant/WebSite共通@id、lastmod更新を確認。
- 状態：公開反映確認済み。
- 未解決：検索側の再取得・表示、AI引用は未確認。確認待ち質問の追加なし。

### 旧Vercel版の重複公開を確認・恒久転送設定を完成（外部反映待ち）
- 対象：旧公開URL https://kyouou-hajime.vercel.app/ 。
- 修正前・確認：2026-10-08の店名検索で旧Vercel版が表示された。旧版は固定「18:00 - 02:00（23:00最終入店）」と「日曜日（不定休あり）」を掲載し、現行正本 https://kyouou-hajime.github.io/ の条件付き翌2時対応・不定休（日曜休業あり）と一致しない。
- 補足：食べログのホームページ欄は同日取得時点で現行GitHub Pages URLへ更新済み。
- 完成物：旧VercelプロジェクトのルートURL「/」を現行公式トップへ恒久転送する vercel.json 案。

```json
{
  "redirects": [
    {
      "source": "/",
      "destination": "https://kyouou-hajime.github.io/",
      "permanent": true
    }
  ]
}
```

- 理由・根拠：旧版へ流れる利用者の営業誤認を防ぎ、公式サイトの参照先を現行URLへ集約するため。Googleはサイト移転時の恒久的なサーバー側301・308転送を推奨している。
  - https://developers.google.com/search/docs/crawling-indexing/301-redirects
- 状態：設定原稿完成／外部反映待ち。現行GitHub Pagesの本文・設定は変更なし。
- 未実施理由：旧Vercelプロジェクトの設定変更・再デプロイは、許可範囲外の外部ホスティング・認証操作を伴うため。
- 検証：旧版と現行版の公開内容、食べログのホームページ欄を公開Webで確認。転送は未反映のためHTTP状態確認は未実施。
- 未解決：Vercel反映後に旧URLが301または308で現行トップへ転送され、旧本文が200表示されないことを確認する。検索結果の切替時期は保証しない。
- 確認待ち質問：追加なし。外部ホスティング・認証操作のため通常質問5件には計上しない。

### ブログ一覧と3記事をBlog構造化データで接続（GitHub反映済み）
- 対象：blog.html、blog-hiyaoroshi.html、blog-nikukai-report.html、blog-ingredients.html、sitemap.xml。
- 修正前：ブログ一覧はBreadcrumbListのみ。個別3記事にはBlogPostingがあったが、記事固有の@idと一覧からの記事関係が未定義。
- 修正後：
  - blog.htmlへBlog構造化データを追加し、名称・URL・説明・発行元・言語を既存表示から設定。
  - BlogのblogPostに、表示中の3記事を記事固有@idで登録。
  - 個別3記事のBlogPostingへ同じ@idを追加し、一覧と記事を機械可読で接続。
  - sitemap.xmlの対象4URLのlastmodを2026-10-08へ更新。
- 理由：記事一覧と各記事の所属関係を検索エンジン・AIへ明示し、店舗Restaurant実体、ブログ、記事の関係を一貫したIDで結ぶため。
- 根拠：Schema.orgはBlogのblogPostプロパティについて「このブログの一部である投稿」と定義し、値にBlogPostingを指定している。
  - https://schema.org/Blog
  - https://schema.org/blogPost
- 変更していないもの：画面本文、記事タイトル、説明、公開日、画像、料理、価格、営業時間、予約条件。
- コミット：
  - blog.html：e6d1460d020261744ac41b8e511b31ae0b4ec5eb
  - blog-hiyaoroshi.html：c754c6d7fa8b8276f589fb70cd467715830ef432
  - blog-nikukai-report.html：040b4a9d5f528fdd1a948cf644ad50877713bbdf
  - blog-ingredients.html：9bcf8ce2476b6b40bcc3bfa63ac4c18394369f78
  - sitemap.xml：694ad0b6a8d447d4798a70131163d8ac35d69488
- 検証：GitHub保存内容を再取得。4ページの全JSON-LD構文解析成功、Blog 1件、BlogPosting 3件、一覧と記事の@id完全一致を確認。sitemap.xmlの対象4URLは2026-10-08へ更新済み。GitHub Pagesのデプロイ成功後、2026-10-08に公開4ページとsitemap.xmlを再取得し、Blog 1件、一覧のblogPost参照3件、個別BlogPostingの@id各1件、lastmod更新4件を確認。
- 状態：公開反映確認済み。
- 未解決：検索側の再取得・表示、AI引用は未確認。確認待ち質問の追加なし。

### アクセスページをRestaurant実体へ接続（GitHub反映済み）
- 対象：access.html、sitemap.xml。
- 修正前：アクセスページの構造化データはBreadcrumbListのみで、ページがトップのRestaurant実体を説明する店舗情報ページである関係が未定義。
- 修正後：WebPage構造化データを追加し、ページ固有@id・正規URL・既存title/description・言語を設定。mainEntityでトップページのRestaurant共通@id、isPartOfでWebSite共通@idへ接続。sitemap.xmlのaccess.htmlのlastmodを2026-10-08へ更新。
- 理由：住所・アクセス・営業時間・電話番号を掲載するページと、公式サイトの店舗実体を検索エンジン・AIへ明示的に関連付けるため。
- 根拠：Schema.orgはmainEntityを「ページ等で説明される主要な実体」と定義し、Restaurantを主要実体とするWebPageの例を掲載している。
  - https://schema.org/mainEntity
  - https://schema.org/docs/datamodel.html
- 変更していないもの：画面本文、住所、営業時間、電話番号、地図、予約URL、料理、価格。
- コミット：
  - access.html：faf1a9b0a7fc77999077da02f88e0d9ea788d129
  - sitemap.xml：35192b217c73dde00082d20667ded9c94138e733
- 検証：GitHub保存内容を再取得し、BreadcrumbList・WebPageのJSON構文解析成功、WebPageのmainEntity/isPartOfがトップページの共通@idと一致、sitemap更新を確認。GitHub Pagesのデプロイ成功後、2026-10-08に公開access.htmlとsitemap.xmlを再取得し、WebPage固有@id、Restaurant/WebSite共通@id各1件、lastmod更新を確認。
- 状態：公開反映確認済み。
- 未解決：検索側の再取得・表示、AI引用は未確認。確認待ち質問の追加なし。

## 2026-10-07

### モバイルの予約メニュー操作領域を拡大（公開反映確認済み）
- 対象：css/style.css。1080px以下で表示される共通モバイルナビゲーション。
- 修正前：メニュー開閉ボタンは文字サイズと上下6px・左右12pxの余白のみ。展開後の各リンクも文字周辺だけが主なタップ領域。
- 修正後：
  - メニュー開閉ボタンへ最小幅・最小高さ48pxを設定し、中央配置。
  - 展開後の全ナビリンクへ幅100%・最小高さ48pxを設定し、各行全体をタップ可能に変更。
  - WEB予約リンクは行内中央に配置。
- 理由：スマートフォンで予約導線を開く入口と、展開後のWEB予約・各ページリンクを押しやすくし、誤タップを減らすため。
- 根拠：Google Android Accessibility Helpは、確実な操作のためクリック・タッチ対象を幅・高さとも48dp以上にすることを案内している。
  - https://support.google.com/accessibility/android/answer/7101858
- 変更していないもの：リンク先、予約URL、電話番号、本文、営業時間、料理、価格。トップページ本文内の予約・電話ボタンは既に最小高さ48pxのため変更なし。
- コミット：07c6b2784203ab1a6554010011be6a9c8f8e3c51
- 検証：GitHub保存内容を再読込し、開閉ボタンとナビリンクの48px指定、リンク幅100%、予約リンク中央配置を確認。CSSの波括弧数一致を確認。GitHub Pagesのデプロイ成功後、2026-10-08に公開CSSを再取得し、48px指定と予約リンク用ルールの反映を確認。
  - 公開CSS：https://kyouou-hajime.github.io/css/style.css
- 未解決：実機ごとのタップ感は未確認。確認待ち質問の追加なし。


### 「丸太町と日本酒」へパンくず構造化データ追加（公開反映確認済み）
- 対象：marutamachi-sake.html。
- 追加：画面表示済みの「トップ ＞ 丸太町で日本酒」を、2階層の `BreadcrumbList` JSON-LDとして追加。
- URL：トップ `https://kyouou-hajime.github.io/`、現在ページ `https://kyouou-hajime.github.io/marutamachi-sake.html`。
- 理由：通常ページ13件のうち、このページだけ画面にパンくずがありながら検索向けパンくずデータがなく、サイト内階層の機械可読情報が不統一だったため。
- 根拠：Google Breadcrumb公式ガイドは、パンくずがページのサイト階層上の位置を示し、検索結果でコンテンツを分類するために使用されると案内している。
  - https://developers.google.com/search/docs/appearance/structured-data/breadcrumb
- 変更していないもの：本文、見出し、タイトル、料理、価格、営業時間、予約条件。
- コミット：fdc88fb3bf7effb96ce7b7596fa98d4ccde0cb6c
- 検証：GitHub保存内容を再読込し、JSON構文解析成功、ListItem 2件の名称・順位・URLが画面表示とcanonicalに一致することを確認。GitHub Pagesのデプロイ成功後、2026-10-07に公開URLを再取得し、BreadcrumbList 1件、現在ページ名・URL各1件の反映を確認。
  - 公開URL：https://kyouou-hajime.github.io/marutamachi-sake.html
- 未解決：検索側の再取得・表示は未確認。確認待ち質問の追加なし。


### ブログ3記事へBlogPosting構造化データ追加（公開反映確認済み）
- 対象：blog-hiyaoroshi.html、blog-ingredients.html、blog-nikukai-report.html。
- 追加：各記事の画面本文・meta情報に既にある見出し、説明、代表画像、公開日を、`BlogPosting` JSON-LDとして明示。
- 追加：`author` と `publisher` に公式トップURLおよびトップページRestaurant実体の共通 `@id: https://kyouou-hajime.github.io/#restaurant` を設定。各記事のcanonical URLを `mainEntityOfPage` に設定。
- 公開日：ひやおろし記事 2026-09-10、食材記事 2026-09-08、肉会記事 2026-09-09。画面表示とブログ一覧の既存日付を照合。
- 理由：従来はパンくず構造化データのみだったため、ブログ記事であること、見出し・画像・公開日・発行主体を検索エンジンへ機械可読で伝えるため。
- 根拠：Google Article構造化データ公式ガイド（2026-09-08更新）は、BlogPostingを対象型に含め、headline・image・datePublished・author等を推奨プロパティとして案内している。
  - https://developers.google.com/search/docs/appearance/structured-data/article
- 変更していないもの：記事本文、表示上の公開日、タイトル、料理、価格、営業時間、予約条件、画像ファイル。dateModifiedは正確な更新日時を画面に掲載していないため追加していない。
- コミット：
  - blog-hiyaoroshi.html：8975c067a68a6d711917958221326e5c8da47799
  - blog-ingredients.html：bb230e5674da5ed7a55e3f93c8d582b2b69fe1aa
  - blog-nikukai-report.html：b9c2ef4bca55b6a404dda37dc8050e8a2a299d85
- 検証：GitHub保存内容を再読込し、3ページともBreadcrumbListとBlogPostingのJSON構文解析成功、各BlogPostingの見出し・説明・画像・公開日・URL・店舗@idが対象ページと一致することを確認。GitHub Pagesのデプロイ成功後、2026-10-07に公開3ページを再取得し、BlogPosting各1件、公開日3件、店舗@id計6件が公開HTMLへ反映されたことを確認。
  - https://kyouou-hajime.github.io/blog-hiyaoroshi.html
  - https://kyouou-hajime.github.io/blog-ingredients.html
  - https://kyouou-hajime.github.io/blog-nikukai-report.html
- 未解決：検索側の再取得・表示、AI引用は未確認。確認待ち質問の追加なし。


### 「酒匠とは」Article構造化データ補強（公開反映確認済み）
- 対象：sakasho.html の Article JSON-LD。
- 追加：記事本文でも使用している代表画像 `https://kyouou-hajime.github.io/images/sake_collection.jpg` を `image` に設定。
- 追加：`author` と `publisher` に公式トップURLと、トップページのRestaurant実体を示す `@id: https://kyouou-hajime.github.io/#restaurant` を設定。店名・組織種別は既存のまま。
- 理由：記事の代表画像と発行主体を検索エンジンへ明示し、トップページの店舗実体と記事の組織表現を同一IDで結ぶため。
- 根拠：Google Article構造化データ公式ガイド（2026-09-08更新）は、適用できる推奨プロパティの追加、記事を代表する `image`、著者を識別する `url` を案内している。
  - https://developers.google.com/search/docs/appearance/structured-data/article
- 変更していないもの：本文、タイトル、料理、価格、営業時間、予約条件、画像ファイル。
- コミット：02dbc0a08437d015ddcdc31abbccd3c4e449f5f6
- 検証：GitHub保存内容を再読込し、JSON構文解析成功、image・author/publisherのURLと@idが意図どおり存在することを確認。GitHub Pagesのデプロイ成功後、2026-10-07に公開URLを再取得し、代表画像1件・店舗@id 2件が公開HTMLへ反映されたことを確認。
  - 公開URL：https://kyouou-hajime.github.io/sakasho.html
- 未解決：検索側の再取得・表示、AI引用は未確認。確認待ち質問の追加なし。


### 昼営業に関するFAQ追加（公開反映確認済み）
- 対象：faq.html。既存9問に「ランチ営業はしていますか？」「最終日曜日の昼飲みは開催していますか？」の2問を追加。新しいページは作成しない。
- 追加回答：
  - 現在、水曜の担々麺ランチは休止しています。通常の夜営業は18:00からです。
  - 最終日曜日の昼飲み企画は終了しました。日曜日の夜営業は、原則として2日前の金曜日までにご予約がある場合に営業します。特別営業日は営業カレンダーをご確認ください。
- 根拠：ユーザーの確定指示（水曜ランチ休止・最終日曜昼飲み終了）、既存の公式FAQの日曜予約条件。llms.txtには既に記載済みだが、来店客向けFAQ本文には未掲載だったため追加。
- 差分：FAQ本文2問と対応するFAQPage JSON-LDを追加。既存9問とそれ以外のHTMLは維持。
- コミット：ac995029a2adde915c3556ccdc94bfcee47f4b22
- 検証：GitHub保存内容を再読込して差分一致を確認。2026-10-07に公開URLを再取得し、本文11問・構造化データ11問、ランチ休止・昼飲み終了の回答がそれぞれ本文とJSON-LDに存在すること、JSON構文解析成功を確認。初回取得は旧9問だったが再取得で新内容を確認。
  - 公開URL：https://kyouou-hajime.github.io/faq.html
- 仕様確認（2026-10-07）：Google公式更新履歴によるとFAQリッチリザルトは2026-05-07終了。今回の目的は利用者が営業状況を確認できる本文整備であり、FAQ検索拡張表示を期待する施策ではない。既存JSON-LDは本文と一致するよう維持。
  - https://developers.google.com/search/updates （2026-05-08・2026-06-15項目）
- 未解決：検索側の再取得・AI引用は未確認。確認待ち質問の追加なし。

### 営業時間の不一致解消（公開確認済み）
- index.html：Restaurant構造化データの固定 `openingHours: 18:00-02:00` を削除。説明に18時開店、最終入店23時、23時までの電話予約等で予約・営業状況に応じ最長翌2時対応を追加。23時を閉店時刻として設定しない。
  - コミット：7ea16945570a52bb8763333377ea89fa46f6b02f
- access.html：店舗情報表とフッターの条件なし「18:00〜翌2:00」を現行の条件付き案内へ変更。
  - コミット：604a11418d090c29c2c42f92d289fde6161e61c2
- menu.html：予約案内・フッターを現行の条件付き案内へ変更。コース2日前予約を維持。料理・価格は変更なし。
  - コミット：fe3b18f3953dd3f8d9a29df4eb9794c524f5e825
- about.html、blog-hiyaoroshi.html、blog-ingredients.html、blog-nikukai-report.html、blog.html、news.html、nikukai.html、sakasho.html：共通フッターを18時開店・最終入店23時、翌2時対応は条件付きに統一。
  - コミット：9ecf66c043d25ff66499217df84c1814666905f2、b63ff9a8649964fdc4bf5bd04ac5009ee0ffd9bd、fd768ab61e480da384241a58fe0c40ef50906650、6754217e3de7756c3541f93cb356676c19edfea3、c4e9f21f5dee31ac6997674f772683bc4a52cde5、e0fb68bbacd612c582e8d786b13723e2343a19ac、332e5787293d21058c8f028587a208c743f3b684、4a34b97df017049b6e5511893ea55b2d6bf3d167
- faq.html：共通フッターを同じ案内に統一。FAQ本文とJSON-LDは維持。
  - コミット：36cd714512611bdaa438cdcf4d93fbc25aa56891
- llms.txt：旧「17時開店・最終入店24時」を現行の条件付き営業時間に訂正。
  - コミット：52222b7558562202a23f023fafaf750d5c9f500b

### アクセス・クロール情報整備（公開確認済み）
- marutamachi-sake.html：本文2か所の徒歩2〜3分を、公式アクセス案内の徒歩3分に統一。
  - コミット：6baef71d4314dc00fa6c4805a6bbb1e0f01340c7
- sitemap.xml：13URLへ確認した更新日を追加。Googleが使用しないpriority/changefreqを除去。URLは増減なし。
  - コミット：20d20e41973fb872ec101c2e864dbd41ac1e95a5

### 今回の追加修正（公開確認済み）
- llms.txt：水曜担々麺ランチ休止、最終日曜昼飲み終了を明記。「酒匠とは」「丸太町と日本酒」の既存ページリンクを追加。
  - 根拠：ユーザーの営業変更指示。既存リンク先はリポジトリ内の実在を確認。
  - コミット：c30c4a71aa06be4a37bf868bcc988573132866bd
  - 注意：llms.txtをAIサービスが利用するかは未確認。利用や引用を保証しない。
- sitemap.xml：徒歩表記を本日修正したmarutamachi-sake.htmlのlastmodを2026-10-06から2026-10-07へ同期。
  - コミット：d8bf27190c8e8f0dd9f5e88cf1211d8ce6852ec4
- SEARCH_CHANGELOG.md：本変更履歴を新設。過去の確認可能な実施記録を集約。店舗向け新ページやナビゲーションは増やさない。

- 公開確認：llms.txtの現況・追加リンク、sitemap.xmlの更新日を公開URLから取得して確認（2026-10-07）。変更履歴はGitHubで保存・再読込を確認。

### 外部店舗ページの営業時間不一致を確認・訂正文完成（外部反映待ち）
- 2026-10-07に公開検索結果を確認。公式HPは現行案内に統一済みだが、外部3ページには固定「18:00〜翌2:00」、日曜定休または全日営業、徒歩2分、ランチ予算表示など、現在の案内と誤認を生む表示が残る。
- 外部アカウント操作は自動実装の対象外のため未変更。各管理画面・情報修正窓口へそのまま使える訂正文を完成させた。

#### 共通の正本（営業時間・営業日）
> 通常18:00開店、最終入店は23:00です。23:00までの電話予約等により、ご予約・営業状況に応じて最長翌2:00まで対応します。定休日は不定休（日曜休業あり）です。日曜日の夜営業は、原則として2日前の金曜日までにご予約がある場合に営業します。特別営業日は営業カレンダーをご確認ください。現在、水曜の担々麺ランチは休止しており、最終日曜日の昼飲み企画も終了しています。

#### PayPayグルメ／一休系ページ向け
> 営業時間を「18:00～2:00（1:00）」から、次の内容へ訂正してください。通常18:00開店、最終入店23:00。23:00までの電話予約等により、ご予約・営業状況に応じて最長翌2:00まで対応します。定休日は不定休（日曜休業あり）。日曜日の夜営業は原則として2日前の金曜日までに予約がある場合に営業し、特別営業日は営業カレンダーを優先します。

#### 食べログ向け
> 曜日ごとの固定「18:00～02:00」は、通常18:00開店・最終入店23:00へ訂正してください。23:00までの電話予約等により、ご予約・営業状況に応じて最長翌2:00まで対応します。定休日は不定休（日曜休業あり）で、日曜日の夜営業は原則として2日前の金曜日までに予約がある場合に営業します。現在、水曜の担々麺ランチは休止し、最終日曜日の昼飲み企画も終了しているため、ランチ営業・ランチ予算の表示も停止してください。アクセスは地下鉄烏丸線「丸太町駅」4番・5番出口から徒歩3分に統一してください。

#### ぐるなび系ページ向け
> 営業時間を固定「18:00～翌2:00」から、通常18:00開店・最終入店23:00へ訂正してください。23:00までの電話予約等により、ご予約・営業状況に応じて最長翌2:00まで対応します。定休日は不定休（日曜休業あり）で、日曜日の夜営業は原則として2日前の金曜日までに予約がある場合に営業します。現在、水曜の担々麺ランチは休止し、最終日曜日の昼飲み企画も終了しています。地下鉄烏丸線「丸太町駅」からの徒歩表記は2分ではなく3分へ訂正してください。

- 確認元：
  - https://paypaygourmet.yahoo.co.jp/114666
  - https://tabelog.com/kyoto/A2601/A260202/26033510/
  - https://kdkx300.gorp.jp/
  - 公式HP正本：https://kyouou-hajime.github.io/access.html および https://kyouou-hajime.github.io/faq.html
- 状態：訂正原稿完成。外部反映は未実施・未確認。
- 確認待ち質問：追加なし。外部アカウント操作は禁止範囲のため、質問5件には計上しない。

### タイトル・説明文点検（変更なし）
- 通常13ページのtitle・meta description・H1を比較。重複や現行営業条件との重大な矛盾は確認されず、件数稼ぎの書き換えは行わなかった。
- 404ページはnoindexでありmeta descriptionなしを維持。

### 20:30〜22:30の来店意図へ日本酒ページを調整（公開反映確認済み）
- 対象：marutamachi-sake.html
- 修正前：
  - 見出し「丸太町で、遅い時間まで日本酒を。」
  - 利用例「京都での夜をもう一軒／遅い時間の食事・酒にも。」
  - FAQ「深夜でも日本酒と料理を楽しめますか？」
- 修正後：
  - 見出し「丸太町で、20:30〜22:30からの食事と日本酒を。」
  - 利用例「20:30〜22:30からのご来店／軽いアテから、しっかり夕食まで。」
  - FAQ「20:30〜22:30からでも食事と日本酒を楽しめますか？」へ変更し、最終入店23時・23時までの電話予約等による条件付き翌2時対応を維持。
- 併せてページ内の店名表記「饗応元」を正式表記「饗応 元」へ統一し、フッターの翌2時対応条件を他ページと同じ文面に揃えた。
- 理由：20:30〜22:30の来店促進を優先し、23時以降の飛び込み客を積極的な集客対象にしない確定方針へ、検索着地ページの訴求を一致させるため。
- コミット：b1cb498877943e8a2a5f91d1bb5576f694f7b409
- 検証：GitHub保存内容の再読込一致を確認。2026-10-07に公開URLを再取得し、新見出し・利用例・FAQが表示され、旧「深夜でも」の質問がなくなったことを確認。
  - 公開URL：https://kyouou-hajime.github.io/marutamachi-sake.html
- 未解決：検索側の再取得・表示、AI引用は未確認。確認待ち質問の追加なし。

### 正式店名「饗応 元」へ表記統一（公開反映確認済み）
- 対象：access.html、blog-hiyaoroshi.html、blog-ingredients.html、blog-nikukai-report.html、blog.html、faq.html、marutamachi-sake.html、news.html、nikukai.html
- 差分：9ページ・42か所の「饗応元」を、正式店名の空白を含む「饗応 元」へ統一。title、meta description、OG/Twitter説明、本文、画像・地図説明、FAQPage JSON-LDを含む。
- 理由：公式サイト内の固有名詞表記を統一し、利用者・検索エンジン・AI検索へ同じ店舗名を一貫して提示するため。
- 内容変更なし：料理、価格、営業時間、住所、予約条件、イベント内容は変更していない。
- コミット：
  - access.html：2ee10fb19b53758f7ecea9a6c1011da6b49058b7
  - blog-hiyaoroshi.html：b0871499564560c6a7101e617dd95c395c031a19
  - blog-ingredients.html：65744bccdec6512081806b362959c475841592e9
  - blog-nikukai-report.html：ada682bb0037d76ee107139d21352b86a3a2b405
  - blog.html：0ed2cb83db45cd345a065ca43da30997ee0f7f13
  - faq.html：b76588c637a4d2ff9fbaa6f1db30c76530ddd199
  - marutamachi-sake.html：6dcc0f2e26ebd3db0e9e64dafd5b4a53994a10bd
  - news.html：b08347547f267d64fd8936547b6cf77b888cce5e
  - nikukai.html：5a8039fb44a16b8f9d0a07a7f65d8a11bafa6275
- 検証：各ファイルをGitHubから再取得し、旧表記0件、正式表記あり、全JSON-LDのJSON構文解析成功を確認。2026-10-07に公開9ページを再取得し、全ページで旧表記0件・正式表記ありを確認。
- 未解決：検索側の再取得・表示、AI引用は未確認。確認待ち質問の追加なし。

### X・SNS共有カード情報を11ページへ補完（公開反映確認済み）
- 対象：about.html、access.html、blog-hiyaoroshi.html、blog-ingredients.html、blog-nikukai-report.html、blog.html、faq.html、marutamachi-sake.html、menu.html、news.html、sakasho.html
- 差分：各ページへ `twitter:card=summary_large_image`、`twitter:title`、`twitter:description`、`twitter:image` を追加。既存のOGタイトル・説明文・画像URLをそのまま同期した。
- 既存状況：index.htmlとnikukai.htmlは同情報を既に実装済みのため変更なし。通常13ページすべてに共有カード情報が揃う構成とした。
- 理由：URL共有時に各ページ固有のタイトル・説明・画像を明示し、SNS側の解釈のばらつきを抑えるため。
- 内容変更なし：ページ本文、料理、価格、営業時間、予約条件、画像ファイルは変更していない。
- コミット：
  - about.html：82cc1c4012902cb420fb7514fa046991b18e6954
  - access.html：5a2c039bfb672de94c1a07e3aef6393b3236b9f7
  - blog-hiyaoroshi.html：1337f7826db444225744e353697c3ff75a7e9bd9
  - blog-ingredients.html：f6f154fbb8b666f2607be1af71812d8c897db11a
  - blog-nikukai-report.html：6d1d447b6c8ac532676be393c4416f4fc9fd73c8
  - blog.html：cffd2c88b3cdf3990bf4bda682fdc135ed403e49
  - faq.html：9e7eb99e6f78350866b55467bb5ef1e6c54f8d51
  - marutamachi-sake.html：733d80f0da01bf60cb3343e793f981bb5c847d07
  - menu.html：19beb9d7867c2d94f8a7b55b2d2ff6cf34dfeac2
  - news.html：2359a867042fc35543e855fbf122e89e2f3ad495
  - sakasho.html：7ee89b26702445b310046ffecc0d203a09e76f14
- 検証：各ファイルをGitHubから再取得。カード指定が各1件で重複せず、X向けタイトル・説明・画像がOG情報と一致することを確認。GitHub Pagesのデプロイ成功後、2026-10-07に公開11ページを再取得し、各ページでcard・title・description・imageが各1件存在することを確認。
- 未解決：各SNS側のキャッシュ更新・実際のカード表示、検索側の再取得は未確認。確認待ち質問の追加なし。

### 点検結果
- リポジトリ内のHTML14ファイル（通常13ページ＋404）を点検。
- 相対内部リンク・画像/CSS/JS参照先に、ファイル欠落は検出されなかった。
- 既存application/ld+jsonはJSON構文解析成功。
- 通常13ページにcanonicalとmeta descriptionを確認。
- この点検は外部URLのHTTP応答、ブラウザ表示、Googleリッチリザルト適格性を保証しない。
- Googleビジネスプロフィール紹介文は変更せず維持。外部アカウント操作・投稿は今回未実施。
- 検索エンジンの再取得・AI引用状況は未確認。

## 2026-10-06（本チャットで確認した過去記録）

- faq.html：遅い時間の予約・日曜営業のFAQとFAQPage JSON-LDを整備。コースは2日前まで。
  - コミット：c8c3a748e4aeffa919f5ee86059121c56f5107a6
- index.html：検索用meta descriptionを店舗特徴・現行予約条件へ更新。
  - コミット：c0de808846b5b2b88b3e7db354b3d75b8aef9240
- index.html：画面上の営業時間・予約案内を条件付き翌2時対応へ統一。
  - コミット：419f4e62e2647aee50c174f5c9dacbd4108290c4
- marutamachi-sake.html：「丸太町で、軽いアテと日本酒を。」の見出し・紹介文・予約導線・説明文・営業時間を更新。
  - コミット：b64375b35b7732f6df01f3b78056da9e705696e4
- 状態：本チャットの実施記録では公開確認済み。今回、過去コミットの全差分を再検証してはいない。

## 自動運用方針（2026-10-07確定）

- 事実確認済み・低リスク・可逆的なHP改善は個別許可なしで実装・公開する。
- 確認が必要な変更は保留して下記質問欄へ記録し、他の安全な改善を進める。
- 未回答の通常質問が5件になったらまとめて確認する。同じ質問を重複計上しない。
- 費用・契約・削除・権限/認証・ドメイン変更・不可逆操作や承認障壁は5件を待たず確認し、許可なしで実行しない。
- 実装、GitHub保存、公開URL確認、検索再取得は別の状態として記録する。
- 既存の検索対策タスクを「饗応 元の毎時検索対策」へ更新。2026-10-07 14:00（日本時間）開始で1時間ごとに改善検討。常駐作業ではなく各実行時に進める。
- 有益な未実施の改善がある場合に実装する。変更や新しい発見がない実行は無理な変更・繰り返し通知をしない。
- 他の投稿・運営タスクの権限や実行時刻は今回変更していない。

## 確認待ち質問

未回答1件。通常質問が5件に達するまでは、当該判断に依存しない安全な改善を継続する。

### Q-001｜WEB予約リンクの着地先（未回答・変更保留）
- 対象：通常13ページにあるWEB予約リンク40件と、index.htmlのReserveAction。
- 質問：一般的な「WEB予約」の着地先は、現在の「お席のみ」専用ページを維持するか、お席のみ・6,400円コース・9,600円コースを選べる店舗予約トップへ統一するか。
- 現状確認（2026-10-08）：
  - 現在のリンク先は全件「お席のみ」専用ページで、ページは正常表示。店名、住所、電話番号も公式HPと一致。
  - 店舗予約トップには「お席のみ」「ショートコース6,400円」「旬のコース9,600円」が表示される。
  - https://res-reserve.com/ja/restaurants/kyouou-hajime-japanesesake/courses/62199736-824e-4a2d-a819-64368d7e5496
  - https://res-reserve.com/ja/restaurants/kyouou-hajime-japanesesake
- 保留理由：お席のみ予約の最短導線を優先するか、コースを含む選択肢を優先するかは集客方針の判断を伴うため、自動変更しない。
- 候補：
  - A：現在のお席のみ直結を維持。
  - B：全件を店舗予約トップへ統一。
  - C：ナビ・トップページはお席のみ直結を維持し、コース説明付近のCTAだけ店舗予約トップへ変更。
- 状態：未回答。リンク切れはなし。変更未実施。

## 次回の優先候補
- 検索向けタイトル・説明文の重複、内容との整合を確認。変更不要なら維持する。
- 実際のブラウザ表示とモバイル予約導線を確認。
- 検索再取得・表示の状況は、利用できる範囲で別途検証。


### 2026-10-08 画像転送量とページ内リンクの点検（改善候補・未実装）
- 対象：index.html、menu.html、images配下。既存の変更記録を確認し、未実施項目として記録。
- 確認結果：GitHub Contents API上のimages/meat.jpgは1,673,684 bytes。トップページで使用され、HTMLの表示寸法指定は3024×4032、loading="lazy"あり。外観333,201 bytes、店内356,411 bytes、日本酒241,232 bytes。写真には既に代替テキストと幅・高さ指定があるため重複修正なし。
- ページ内リンク：index.htmlとmenu.htmlのhref="#..."は全て同ページのidに対応。欠落なし。
- 次回の優先候補：meat.jpgの表示サイズに適した圧縮画像・レスポンシブ画像を作成し、元画像と見比べて画質確認後に差し替える。ファイル容量だけから実際の読み込み時間やCore Web Vitalsへの影響は断定しない。
- 未実施理由：現在利用可能なGitHubのファイル作成・更新機能はUTF-8テキストのみで、圧縮したバイナリ画像の公開に利用できない。画像差し替え、HP本文、sitemapの更新は行っていない。
- 状態：点検完了／画像軽量化は未実装。検索対策の実装件数には数えない。
- コミット：本記録を追加したコミットをGitHub履歴で参照。
- 未解決：画像の実表示サイズと画質、圧縮後容量、公開後の読み込み検証。確認待ち質問の追加なし。


### 2026-10-08 予約・再来店・写真・評判・効果測定を統合（HP公開確認済み・原稿完成）
- ユーザー指示：検索対策以外の予約・来店率、再来店、写真/SNS導線、口コミ、測定を組み込み、今できる範囲を進める。
- 対象：index.html、GROWTH_OPERATIONS.md、既存毎時タスクのプロンプト。時間・雨判定・安全境界は維持。
- 修正前：トップの店内・食材・日本酒写真の直後に予約・メニュー・最新情報の操作ボタンがなかった。
- 修正後：写真直後に「料理・メニューを見る」→menu.html、「お席・予約方法を確認」→#reservation、「最新の料理・日本酒を見る」→公式Instagramの3ボタンを追加。軽いアテと一杯〜夕食、20:30〜22:30利用案内を追加。既存48px以上のボタンCSSを再利用。
- 理由：写真を見て関心を持った利用者が、メニュー確認・予約へ進める位置に導線を設ける。効果は未測定。
- 完成原稿：GROWTH_OPERATIONS.mdに会計時の再来店案内、任意の口コミ依頼、任意の初来店経路質問、個人情報なし・1組単位の店内集計方法、ストーリーズ予約誘導文を保存。外部投稿・顧客送信・集計収集は未実施。
- 根拠：店舗確定情報と既存公式リンク。Google口コミガイドは率直な実体験の依頼を認め、見返り付き依頼を禁止：https://support.google.com/business/answer/3474122?hl=ja 。口コミ星数指定・依頼相手の満足度による選別はしない。
- コミット：index.html 3b5531ff30a5d26a44cc80259569033986ed6084、GROWTH_OPERATIONS.md 508972376b47adcb7d1336f3b2a384297dfd33ba。本記録のコミットはGitHub履歴参照。
- 検証：GitHub保存後のindex.htmlと原稿を再取得し完全一致を確認。index変更のPages run 37730946493成功。公開トップで3ボタンと利用案内を確認し、予約案内ボタンをクリックして公開URL https://kyouou-hajime.github.io/#reservation へ到達確認。既存CSSのモバイル2列・第1ボタン全幅とmin-height48pxを確認。実機でのタップ感は未確認。
- 状態：HPの追加導線は公開反映確認済み。再来店・口コミ・ストーリーズ・測定は原稿完成／実運用未確認。毎時タスクへの追加保存成功。
- 未解決：口コミ投稿専用リンク、予約先Q-001、画像軽量化は従来どおり保留。実計測・予約増加・検索側再取得は未確認。次回優先：新導線のモバイル確認と、取得できた実集計に基づく改善。追加質問なし。


### 2026-10-08 HPセキュリティ強化：14ページへCSP追加（デプロイ成功・公開トップ確認済み）
- ユーザー指示：HPのハッキング対策を強化する。
- 修正前：14ページにCSPなし。実行JavaScriptはjs/main.jsのナビ開閉のみ。インライン実行コード・on*イベント属性・フォーム・baseタグ・javascript:リンクなし。検索データはapplication/ld+json。
- 修正後：各ページのcharset直後へ、script-src 'self'; object-src 'none'; base-uri 'none'; form-action 'none' のmeta CSPを追加。外部・インラインJSとeval等、object/embed、baseタグ、フォーム送信を制限。外部予約は通常リンクのため対象外。CSS・写真・フォント・Googleマップを読み込む制限は今回は追加しない。
- 対象：404.html、about.html、access.html、blog-hiyaoroshi.html、blog-ingredients.html、blog-nikukai-report.html、blog.html、faq.html、index.html、marutamachi-sake.html、menu.html、news.html、nikukai.html、sakasho.html。Google所有権確認ファイルは変更なし。
- 根拠：https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy 。非JavaScript MIMEのscriptはデータブロックとして扱う：https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/script 。
- 検証：14ページの保存後内容を再取得し期待内容と完全一致、全JSON-LD構文解析成功。js/main.jsはイベント登録のみでeval/HTML挿入/外部依存なし。現在のテキストファイルで典型的なGitHubトークン・AWSアクセスキー・秘密鍵パターンは検出なし（限定的な点検で、履歴・画像・圧縮ファイル・全種類の秘密を保証しない）。
- 毎時運用：セキュリティ点検を追加。2FA・権限・認証・ホスティング変更は自動実施しない。
- コミット：
  - 404.html：d466c975f88799773812983efff2222ae0d0d1a1
  - about.html：8b7f91b2c0d076b24c001ab78bbe52e475d8bf7c
  - access.html：1b08ff3f08c48bbd768b341999db0d78189ce294
  - blog-hiyaoroshi.html：889e901794edecef8ca3608190b543f09e311921
  - blog-ingredients.html：bc8434ed0dc9c6c85d3a5c82ea9f661135ed7ae6
  - blog-nikukai-report.html：f686acc65e555366fb092bf7bf35f124e501b5c2
  - blog.html：32f6188c178546b359df6cfd9962b24613622e36
  - faq.html：9035b6f55bf4fe895db0054f8cb7cf0aad305109
  - index.html：9eb013d1bbe465b3a09867063a636b870f1d38ea
  - marutamachi-sake.html：b70651f48b1f636a7d8d4c0c7719527dacd38d70
  - menu.html：5f1e7b5113989c2981e5478b53a6a72b274b4f9b
  - news.html：705a94a1340dc6ad829801881eb24b29d7daea91
  - nikukai.html：593431f2b00a8060968b0f406b87c23db2353d99
  - sakasho.html：45949c06552913638ff7b85ae6ab6268e33a280f
- 状態：14ページのGitHub保存・静的検証済み。Pages run 37731698466の成功を確認。2026-10-08の公開トップでCSP一致、JSON-LD解析成功、js/main.js参照、写真4枚の読み込み、写真直後の予約案内ボタンから/#reservationへの到達と外部予約リンク維持を確認。続けて残り13ページを公開URLで個別確認し、全14ページで同一CSPの公開反映を確認。通常13ページの全JSON-LDは構文解析成功、全通常ページでjs/main.jsのみを実行スクリプトとして確認。404ページは実行スクリプト・JSON-LDなしの設計を維持。Googleマップ埋め込みは公開access.htmlで486×303pxの表示領域、地図データ・利用規約等のフレーム内要素を確認し、CSP追加後も読み込み成功を確認。実機モバイル操作は未確認。検索側再取得は未確認。
- 限界：meta CSPはframe-ancestors等のHTTPヘッダー専用保護を提供しない。GitHubアカウントや同一オリジンの正規ファイルを乗っ取られた場合の防御ではない。アカウント2FA・保護ルール・トークン権限・ログイン状況は未確認。攻撃や漏えいの存在を断定しない。
- 次回優先：未確認の実機モバイルナビ操作を確認し、今後の新ページでもCSPを維持する。実装前の元内容は各コミットの親から復元可能。
