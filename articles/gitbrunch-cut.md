---
title: "ブランチを切って、プルリクエストを送ってみた"
emoji: "🐙"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [git, Github]
published: false
---

# 前提条件

- mac OS
- プログラミング勉強期間が 3 ヶ月ほど
- https://github.com/Utopia300/UOZUMI-Fatigue-measurement
  → 現在開発中のこちらで実際に試してみた

# なぜブランチを切って、プルリクエストを送ってみたのか？？

現在初のチーム開発を行っており、その際に使用するため、先に一人で練習しました.

# 今回参考にした記事

https://qiita.com/Taku07/items/8c38038b56007de7caca
https://qiita.com/samurai_runner/items/7442521bce2d6ac9330b
上記の記事を参考に実際にてみたら割と簡単にできました。
下にやり方をまとめていますが、それぞれの記事を参考にしてみてください。

# やり方

## ブランチの確認と、作成

`$ git branch`
で現在のブランチを確認する。

`$ git branch 新しいブランチ名`
で新しいブランチを作成する。

(例)`$ git branch develop `

## プルリクエストの送信

① 編集ファイルをステージングに移す
`$ git add .`

② 編集ファイルを commit する
`$git commit -m "update README"`

③develop ブランチから Github 上の origin ブランチに push する
`$git push origin develop`

④GitHub でプルリクエスト操作を行う

# 最後に

今回の内容は以上になります。
僕みたいに個人開発ばかりして、チーム開発をまだやったことがない方も多いと思いますので、これを機会に、自分で実際に試してみてください。

それではまた。
