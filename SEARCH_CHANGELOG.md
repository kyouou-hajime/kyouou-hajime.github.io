# 饗応 元｜検索対策・HP変更履歴

日付は日本時間。原稿完成・GitHub反映・公開ページ確認・検索側の再取得を区別する。
各変更の差分は記載のコミットとGitHub履歴で確認できる。順位上昇・AI引用は保証しない。
安全な修正はユーザーの包括的な許可（2026-10-07）に基づいて実施する。料金・未確認情報・外部アカウント設定などは推測で変更しない。

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

現時点で、この欄へ登録した未回答質問は0件。
新しい項目は質問ID・対象・質問内容・保留理由・候補・状態を記録する。回答後も履歴を削除せず、回答と処理結果を追記する。

## 次回の優先候補
- 検索向けタイトル・説明文の重複、内容との整合を確認。変更不要なら維持する。
- 実際のブラウザ表示とモバイル予約導線を確認。
- 検索再取得・表示の状況は、利用できる範囲で別途検証。
