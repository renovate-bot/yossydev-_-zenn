---
title: "React Hooksについての勉強メモ"
emoji: "🔖"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [react, nextjs]
published: false
---

内容で間違ってる点や、変な箇所がございましたら、お知らせください。

# 前回のブログはこちら
https://zenn.dev/yuto76/articles/nextjs-react


## ユウトって誰？？？
- apple信者なので、macOS
- プログラミング勉強始めて4ヶ月くらい
- サッカーが大好き

## このブログを書く経緯
- チーム開発で、Reactに関してまだまだ理解できていないと感じた
- ただ復習するだけでは効率が悪いと感じ、ブログを書くことにした

## 本題
[公式ドキュメント](https://ja.reactjs.org/docs/hooks-reference.html)

### ■ useCallback

- useCallback を用いると、処理自体は変わらないが、再レンダリングされた時に再生成されなくなる
- コンポーネント内部に書いても、パフォーマンスがそこまで悪くならない

```jsx
// コンポーネント内部に書く場合、再レンダリングされて、パフォーマンスが悪くなってしまう
export const Home = () => {
  const handleClick = () => {
    alert('クリック！');
  },

  return (
    <div>
      <button onClick={handleClick} />
    </div>
  );
};
```

```jsx
// useCallback を使うことで、無駄な再レンダリングを防ぐ
export const Home() => {
  const handleClick = useCallback(() => {
    alert('クリック！');
  }, []);

  return (
    <div>
      <button onClick={handleClick} />
    </div>
  );
};
```

### ■ useEffect (マウント / アンマウント)

- 一番最初にコンポーネントが表示される（マウント）
- コンポーネントが何かしらの処理で消えてしまう（アンマウント）
- useEffect 内部で、マウント時と、アンマウント時の処理を記述できる

```jsx
export const Home = () => {
  useEffect(() => {
    alert('マウント！');
    return () => {
      alert('アンマウント！');
    };
  }, []);
};
```

### ■ useState (state = 状態)

- state を使わず記述をすると、値は更新されるが、ページ上では更新されない
  → 理由：React のコンポーネントは、状態が変化しないとコンポーネントが再レンダリングされないようになっている
- コンポーネントを再レンダリングさせるために、state を使う

```jsx
// useStateを使わない
export const Home = () => {
  let count = 1;

  const handleClick = () => {
    count = count + 1;
  };

  return (
    <div>
      <p>{count}</p>
      <button onClick={handleClick} />
    </div>
  );
};
// 実際に値は変わっているが、コンポーネントは再レンダリングされないため、ページ上は変化しない
```
```jsx
// useStateを使う
export const Home = () => {
  const [count, setCount] = useState(1);

  const handleClick = () => {
    setCount((count) => count + 1);
  };

  return (
    <div>
      <p>{count}</p>
      <button onClick={handleClick} />
    </div>
  );
};

// stateによって、コンポーネントが再レンダリングされるため、ページの値も変化する
```
### ■ useEffect / useCallback の第二引数の空配列について

#### useEffect

- useEffect の第二引数の[]に変数を入れると、その変数が変更されたタイミングで、改めて useEffect の部分の処理が走る
- 第二引数に何かしらの値を入れても、アンマウントの処理は実行される
- アンマウント（Cleanup Function）→ マウントの順番で処理が走る
- 配列なので、いくつでも変数を入れることができる

```jsx
export const Home = () => {
  const [count, setCount] = useState(1);

  const handleClick = () => {
    setCount((count) => count + 1);
  };

  useEffect(() => {
    alert('マウント！');
    return () => {
      alert('アンマウント！');
    };
  }, [count]);
};

// アンマウント→マウントの順番で処理が走る
```

#### useCallback

- useCallback で、第二引数に何も入れなかったら、その中身がずっと同じ状態になる（useCallback は再生成されないため）

```jsx
export const Home = () => {
  const [count, setCount] = useState(1);

  const handleClick = () => {
    setCount((count) => count + 1);
  };

  const handleClick = useCallback(() => {
    if (count > 10) {
      setCount((count) => count + 1);
    }
  }, [count]);
};

// この場合、10以上は画面に表示されない
// 第二引数の[count] がない場合、10以降もそのまま画面に表示される
```

#### なぜ、第二引数に変数を指定して、更新・再生成させたりという処理が必要なのか？

- パフォーマンスのため
  (更新させたいものは変数を指定し、更新させなくてもいいものは空にする)

## まとめ

今回はReact HooksのuseState, useEffect, useCallbackの基礎の復習をしました。
それぞれの使い方や、マウント/アンマウント、第二引数の意味など、すごい学びのある復習になりました。

理解したつもりでいても、実際は理解できていないことだらけだと思うので、これからも引き続き勉強していって、ブログも更新していこうと思ってます.

