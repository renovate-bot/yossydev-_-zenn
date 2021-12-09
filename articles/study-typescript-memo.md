---
title: "[TypeScript]基本の型"
emoji: "😊"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [TypeScript]
published: false
---

最近 TypeScript のインプットが多くなってきたので、整理のためにまとめました。

:::message alert

#### この記事でやらないこと

- TypeScript とはみたいな概念理解
- 実践的な TypeScript の使い方

これらはまた別で記事にしたいと思っています
:::
この記事の最後に、参考にした記事を載せておきます。

## TypeScript の型（基本）

### プリミティブ型

TypeScript 以下の型 7 つをプリミティブ型と呼びます。

#### 文字列型(string)

文字列のみを受け取る型

```tsx
const str: string = "Hello, TypeScript!";
const str: string = 111; // error
```

#### 数値型(number)

数字のみを受け取る型

```tsx
const num: number = 0;
const num: number = "Hello, TypeScript!"; // error
```

#### 論理型(boolean)

真偽値(true/false)のみを受け取る型

```tsx
const bool: boolean = true;
const bool: boolean = false;
const bool: boolean = "Hello, TypeScript!"; // error
```

#### undefined 型

undefined のみを受け取る型

```tsx
const undef: undefined = undefined;
const undef: undefined = null; // error
```

#### null 型

null のみを受け取る型

```tsx
const null: null = null;
const null: null = undefined; // error
```

#### symbol 型と bigint 型

後は他にも symbol 型と bigint 型がありますが、あまり見たことがなく、参考にした記事でもそこまで深く書かれていなかったので、今回は割愛させていただきます。

### オブジェクト型

TypeScript では、プリミティブ型以外の型をオブジェクト型と呼びます。

#### any 型

#### void 型

#### object 型

#### 配列型
