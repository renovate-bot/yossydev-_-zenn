---
title: "ReactのPropsについての勉強メモ"
emoji: "🌊"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [react,nextjs]
published: true
---

内容で間違ってる点や、変な箇所がございましたら、お知らせください。

## ユウトって誰？？？
- apple信者なので、macOS
- プログラミング勉強始めて4ヶ月くらい
- サッカーが大好き

## このブログを書く経緯
- チーム開発で、Reactに関してまだまだ理解できていないと感じた
- ただ復習するだけでは効率が悪いと感じ、ブログを書くことにした

### Props 前半

- props は、親から渡ってきたデータ
- props を用いることで、動的にデータを出し分けすることができる
- props はいくつでも渡せる

```jsx
// 例)
// ../components/Header.jsx
export const Header = (props) => {
  return (
    <div>
      <h1>{props.title}</h1>
      <p>{props.description}</p>
    </div>
  );
};

// ./index.jsx
export default Home() => {
  return (
    <div>
      <Header title="Next.js" description="React のフレームワークです" />
    </div>
  );
};

// props.title = "Next.js"
// props.description = "React のフレームワークです"
```

### Props 後半

- 文字列は""、数字は{}、配列は[]、オブジェクトは{{}}、boolean は {true/false}
- コンポーネントをそのまま渡すこともできる

```jsx
// 例） コンポーネントを渡す
<Header components={<div>foo</div>} />
```

- 関数も渡せる

```jsx
// 例） 関数を渡す
// ../components/Header.jsx
export const Header = (props) => {
  return (
    <div>
      <button onClick={props.onClick}></button>
    </div>
  );
};

// ./index.jsx
export const Home() => {
  return (
    <div>
      <Header onClick={() => alert('クリック！')} />
    </div>
  );
};
```

- Children でも渡せる

```jsx
// 例） Children を渡す
// ../components/Header.jsx
export const Header = (props) => {
  return (
    <div>
      {props.children}
    </div>
  );
};

// ./index.jsx
export const Home() => {
  return (
    <div>
      <Header>
        foo
      </Header>
    </div>
  );
};

// propsでfooが渡される
// コンポーネントを渡す際は、childrenを使うことが多い
```

## まとめ
今回の復習で、以前まではノリと気合で書いていたコードがだいぶ理解できた気がします。
これからは応用できるよう、自分の過去のコードを見たり、色々な方のコードを見たりして、引き続き勉強していきます。

次回はReact Hooksについて復習です。