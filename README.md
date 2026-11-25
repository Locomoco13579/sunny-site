# Sunny 専用サイト（公開手順書）

住所の案：`https://sunny.one-loop-inc.com/`　置き場：GitHub Pages（無料・リポジトリ Locomoco13579/sunny-site）。
このリポジトリの main の / がそのまま公開されます（ビルド不要の静的ファイル）。

## 中身と公開後の URL

| ファイル | 公開後の URL | 使い道 |
|---|---|---|
| index.html | https://sunny.one-loop-inc.com/ | App Store「開発者ウェブサイト」（Marketing URL）・Steam の公式 URL |
| privacy/ja/index.html | https://sunny.one-loop-inc.com/privacy/ja/ | App Store「プライバシーポリシー URL」（日本語） |
| privacy/en/index.html | https://sunny.one-loop-inc.com/privacy/en/ | 同（英語）。/privacy/ は言語の選択ページ |
| support/ja/index.html | https://sunny.one-loop-inc.com/support/ja/ | App Store「サポート URL」（日本語） |
| support/en/index.html | https://sunny.one-loop-inc.com/support/en/ | 同（英語）。/support/ は言語の選択ページ |
| app-ads.txt | https://sunny.one-loop-inc.com/app-ads.txt | AdMob の app-ads.txt（1行） |
| robots.txt / CNAME / .nojekyll | — | クロール許可／独自ドメイン指定／Jekyll を無効化（.txt は標準で text/plain） |

問い合わせ先メールは `support@oneloopinc.net`（窓口用）。変えるときは privacy と support の4ページを直す（検索で `oneloopinc.net`）。

## app-ads.txt とサブドメイン（調べた結果）

- Google は、ストアに登録した「開発者ウェブサイト」の**ホスト名**から `https://<ホスト>/app-ads.txt` を探す。`sunny.one-loop-inc.com` なら **まず sunny.one-loop-inc.com、次に one-loop-inc.com** を見る（サブドメインは1段まで。`www.` `m.` は無視）。
- したがって **サブドメインのままでよい。ルート（one-loop-inc.com）に置く必要はない**。ただし、開発者ウェブサイトに登録する URL は `sunny.one-loop-inc.com` にすること（www や別ホストにしない）。
- 出典：Google AdMob ヘルプ https://support.google.com/admob/answer/9363762 、実装の案内 https://developers.google.com/admob/ios/app-ads
- 代案（不要の見込み）：ルート one-loop-inc.com は Wix なので、ルートに置くには Wix 側のリダイレクトが要り面倒。サブドメイン運用ならこの問題を避けられる。
- 注意：Google が拾うまで最大24時間以上かかることがある。リダイレクトを挟むなら1回まで。

## 公開の仕組みと、マスターがやること

- GitHub Pages は設定済み（main の /、カスタムドメイン sunny.one-loop-inc.com）。
- マスターが Wix の DNS に入れる：種類 `CNAME`／名前 `sunny`／値 `locomoco13579.github.io`
- DNS が通ったら、リポジトリの Settings → Pages で「Enforce HTTPS」にチェックを入れる。
- 確認：https://sunny.one-loop-inc.com/ 、/privacy/ja/ 、/app-ads.txt
- ストア登録：App Store Connect の開発者ウェブサイト＝`https://sunny.one-loop-inc.com/`、サポート URL＝`/support/ja/`、プライバシー URL＝`/privacy/ja/`。AdMob は app-ads.txt の反映を待つ。

## 更新するとき
ファイルを直して main に push すれば、数分で反映される。
