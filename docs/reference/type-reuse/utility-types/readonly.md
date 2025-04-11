---
description: 全プロパティを読み取り専用にする
title: Readonly<T>
---

`Readonly<T>`は、オブジェクトの型`T`のプロパティをすべて読み取り専用にするユーティリティ型です。

## Readonly&lt;T>の型引数

### T

型引数`T`にはオブジェクトの型を代入します。

## Readonlyの使用例

```ts twoslash
type Person = {
  surname: string;
  middleName?: string;
  givenName: string;
};
type ReadonlyPerson = Readonly<Person>;
//    ^?
```

上の`ReadonlyPerson`は次の型と同じになります。

```ts twoslash
type ReadonlyPerson = {
  readonly surname: string;
  readonly middleName?: string;
  readonly givenName: string;
};
```

## Readonlyの効果は再帰的ではない

`Readonly<T>`が読み取り専用にするのは、オブジェクトの型`T`直下のプロパティのみです。プロパティがオブジェクトだった場合、それが持つプロパティまでは読み取り専用にならないので注意してください。

## Readonlyの実装

`Readonly<T>`は次のように実装されています。

```ts twoslash
// @noErrors: 2300
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};
```

## 関連情報

[オブジェクト型のreadonlyプロパティ (readonly property)](../../values-types-variables/object/readonly-property.md)

[クラスのreadonly修飾子](../../object-oriented/class/readonly-modifier-in-classes.md)

[インターフェースのreadonly修飾子](../../object-oriented/interface/readonly-modifier-in-interfaces.md)

[readonlyとconstの違い](../../values-types-variables/object/readonly-vs-const.md)
