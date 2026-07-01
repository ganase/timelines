# Timelines MVP

時刻を縦軸、アカウントを横軸にした Bluesky 対応タイムライン UI です。

## 開き方

`index.html` をブラウザで開くと、サンプルデータ付きで表示できます。

## 実装済み

- 現在時刻を最上部に表示
- 1分ごとに現在分を更新し、Bluesky 投稿をロード
- デフォルトで直近60分を表示
- 下部の「さらにロード」で過去60分を表示し、取得済みカーソルから古い投稿を追加ロード
- 右上の `+` ボタンから表示アカウントを追加
- Bluesky の公開プロフィール取得と投稿ロード
- Bluesky app password 認証
- 画面下部の投稿欄から自分の Bluesky アカウントへ投稿
- 登録アカウント、セッション、投稿キャッシュを `localStorage` に保存
- 同じアカウントが同じ1分内に複数投稿した場合は縦に圧縮表示
- 投稿文字列は1行省略表示
- 投稿にマウスオーバー、またはタップ/クリックすると全文をポップアップ表示

## 認証について

右上の「未認証」ボタンから Bluesky にログインします。

- 通常パスワードではなく Bluesky の app password を使ってください。
- app password 自体は保存しません。
- ログイン状態を保存する場合、Bluesky の `accessJwt` と `refreshJwt` をブラウザの `localStorage` に保存します。
- 共有端末ではログアウトしてください。

## 公開環境

この MVP はサーバーなしの静的 HTML なので、無料公開は GitHub Pages が第一候補です。

このリポジトリには `.github/workflows/pages.yml` を追加済みです。GitHub Pages を GitHub Actions から公開する設定にすると、`main` への push 後に `https://ganase.github.io/timelines/` で公開できます。

OpenAI / Codex はこのアプリを外部公開するための汎用静的ホスティングではないため、外からアクセスする公開先としては GitHub Pages、Cloudflare Pages、Vercel、Netlify などを使う想定です。

## 制限

- X / Twitter は API キーと有料 API 条件が必要になりやすいため、現状は列登録のみです。
- Bluesky OAuth の完全実装ではなく、MVP として app password 認証を使っています。
- セキュリティを強める場合は、将来的に OAuth + 小さなバックエンドへ移行してください。
