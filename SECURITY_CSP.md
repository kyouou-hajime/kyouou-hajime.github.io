# CSP・セキュリティ確認記録（2026-10-14）

対象: GitHub Pages `https://kyouou-hajime.github.io/`、リポジトリの公開用HTML。

## 変更

公開用のHTML 17ページ（404、トップ、料理・酒、日本酒漫画、アクセス、各記事など）の `<meta http-equiv="Content-Security-Policy">` を統一した。Googleのサイト所有権確認用HTML 2ファイルは検証用の固定内容を維持した。

```text
default-src 'none'; script-src 'self'; style-src 'self' https://fonts.googleapis.com 'unsafe-inline'; img-src 'self' data:; font-src https://fonts.gstatic.com; connect-src 'none'; frame-src https://www.google.com; object-src 'none'; base-uri 'none'; form-action 'none'
```

| 対象 | 実際の読み込み・動作 | 許可 |
| --- | --- | --- |
| JavaScript | `js/main.js`。JSON-LDは実行スクリプトではない | `script-src 'self'` |
| CSS | 自サイトのCSS、Google FontsのCSS、漫画ページの`<style>`、数ページの`style`属性 | `style-src 'self' https://fonts.googleapis.com 'unsafe-inline'` |
| 画像 | 自サイトの料理写真、漫画WebP、メニューアイコン、CSS中の`data:` SVG | `img-src 'self' data:` |
| フォント | Google Fontsが配信するフォント | `font-src https://fonts.gstatic.com` |
| iframe | トップとアクセスのGoogleマップ | `frame-src https://www.google.com` |
| fetch等の通信 | 公開用JSには外部API通信なし | `connect-src 'none'` |
| 予約・Instagram・翻訳・地図リンク | 別サイトへの通常の遷移。電話は`tel:` | リソースの読み込み先ではないため、上記の許可リストに含めない |

以前は`script-src`、`object-src`、`base-uri`、`form-action`だけだったため、画像・CSS・フォント・iframe・通信はCSPによる明示的な読み込み元制限がなかった。今回の`default-src 'none'`により、列挙していない種類のリソースも原則拒否される。`'unsafe-inline'`は既存の行内CSSの表示を維持するため、CSSに限って残した。実行可能な行内JavaScriptは許可していない。

## 検証した範囲

- 変更前: GitHubの公開用HTML 17ページと`css/style.css`、`css/home.css`、`js/main.js`を調査。実行スクリプトは自サイトの`js/main.js`、外部スタイルはGoogle Fonts、外部iframeはGoogleマップのみ。行内の実行JavaScriptはなし。
- 変更前: 公開トップのHTTP応答には`Content-Security-Policy`ヘッダーがなく、HTMLのmetaで旧ポリシーが設定されていた。GitHub Pagesの配信側にHSTSヘッダーはあった。
- 変更後: GitHub上の17ページに同一ポリシーを配置し、metaタグが最初のリソース読み込みより前にあることを静的に確認。
- 変更後: 公開トップ、料理・酒、漫画ページに新ポリシーが配信されたことをブラウザーで確認。トップの写真4点と地図の埋め込み、メニュー冒頭の写真6点、漫画「生酒」の3画像が読み込まれた。Google Fontsの読み込み完了状態、メニューの予約・電話リンク先、漫画のテーマ移動も確認。これらの操作でサイト由来のCSP違反ログは観測されなかった。
- 外部予約サイトで予約を確定する操作、電話発信、すべての漫画画像の拡大、全ページの全画面での実機表示は行っていない。リンク先の存在とブラウザーの表示確認を、予約完了・通話完了とは扱わない。

## GitHub Pagesの制約

公開サイトの応答に任意のHTTPセキュリティヘッダーをリポジトリの`_headers`等から付与する設定は確認できなかった。今回のCSPはHTMLのmeta方式なので、そのタグの読み込み後に適用される。`frame-ancestors`（他サイトによる埋め込み制限）、`report-uri`/`report-to`（違反報告）、`Content-Security-Policy-Report-Only`、その他HTTPヘッダー依存の制御は、この方式では実現できない。これらが必要なら、HTTP応答ヘッダーを設定できる配信基盤・前段プロキシが必要。

今後、外部画像・フォント・スクリプトやiframeを追加するときは、実際の配信元を確認してから17ページのポリシーを更新し、公開ブラウザーで再確認する。行内CSSを外部CSSに整理すれば、将来`style-src`から`'unsafe-inline'`を外せる。
