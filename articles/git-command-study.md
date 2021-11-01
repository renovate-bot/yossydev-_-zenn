---
title: "[超入門]Gitの使い方"
emoji: "🌊"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [Git, Github]
published: false
---

# [超入門]git の使い方

ずっと vscode の git 機能を使っていたのですが、最近サロン内でチーム開発をいただく機会があったので、その際に git の使い方を色々と勉強になったので、アウトプットのために色々書いていきます。

内容はめちゃくちゃ基礎的なことなので、僕みたいいな初心者むけの内容となっています。

### おすすめの記事

https://qiita.com/kohga/items/dccf135b0af395f69144

## ■git command

#### インデックスにコミットしたいファイルを登録する。

```
$ git add .
```

#### インデックスにあるファイルを更新する。

```
$ git commit -m ""
```

#### ローカルリポジトリの内容をリモートリポジトリに送信する

```
$ git push origin <ブランチ名>
```

#### リモートから変更を取得する

```
$ git pull
```

#### ローカルの変更を確認する

```
$ git status
```

#### ローカルでブランチを作成

```
$ git branch <ブランチ名>
```

#### ローカルでブランチを切り替え

```
$ git checkout <ブランチ名>
```

#### ブランチ作成 & 切り替え

```
git checkout -b <ブランチ名>
```

#### ブランチをマージする

```
$ git merge <ブランチ名>
```