---
title: "TailwindCSSのreset cssを一時的に消す方法"
emoji: "🙆"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [TailwindCSS]
published: true
---

# 結論

こちらのプラグインを使います。
https://github.com/tailwindlabs/tailwindcss-typography

方法は他にもあるかと思いますが、僕はこれで上手く表示をさせれました.

正直、こちらの上記を見た方が確実です。
どうしてもわからない方は、比べながら見てください。

## 前提条件

- Next.js + TailwindCSS + microCMS を使って web サイトを製作中に blog 機能を追加した
- プログラミング勉強期間 3 ヶ月

（作成したサイトはこちら）
https://uozumi-fc.vercel.app/
https://github.com/Utopia300/UOZUMI-FC

## 一応説明

こちらをインストール
`$ npm install @tailwindcss/typography`

そして次に、tailwind.config.js をこのように編集します

````// tailwind.config.js
module.exports = {
  theme: {
    // ...
  },
  plugins: [
    require('@tailwindcss/typography'),
    // ...
  ],
}```
````

あとは reset css を消したい部分に、
`className="prose"`
と記入すれば大丈夫です。

# 最後に

今回初めて TailwindCSS を使ったのですが、便利すぎてびっくりしました。
これからもお世話になろうと思います。
