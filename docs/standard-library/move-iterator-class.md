---
title: move_iterator クラス | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::move_iterator
- iterator/std::move_iterator::iterator_type
- iterator/std::move_iterator::iterator_category
- iterator/std::move_iterator::value_type
- iterator/std::move_iterator::difference_type
- iterator/std::move_iterator::pointer
- iterator/std::move_iterator::reference
- iterator/std::move_iterator::base
dev_langs:
- C++
helpviewer_keywords:
- std::move_iterator [C++]
- std::move_iterator [C++], iterator_type
- std::move_iterator [C++], iterator_category
- std::move_iterator [C++], value_type
- std::move_iterator [C++], difference_type
- std::move_iterator [C++], pointer
- std::move_iterator [C++], reference
- std::move_iterator [C++], base
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e72f9c584f818de69b0c341ff8dba66892816d8a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
---
# <a name="moveiterator-class"></a>move_iterator クラス

クラス テンプレート `move_iterator` は反復子のラッパーです。 move_iterator は、ラップする (格納する) 反復子と同じ動作を提供します。ただし、格納されている反復子の逆参照演算子を右辺値参照に変換して、コピーを移動を切り替えます。 右辺値の詳細については、「[右辺値参照宣言子: &&](../cpp/rvalue-reference-declarator-amp-amp.md)」をご覧ください。

## <a name="syntax"></a>構文

```cpp
class move_iterator;
```

## <a name="remarks"></a>コメント

このテンプレート クラスは、逆参照時以外は反復子のように動作するオブジェクトを表します。 これは、メンバー関数 `base()` を介してアクセスされる `Iterator` 型のランダム アクセス反復子を格納します。 `move_iterator` に対するすべての操作は、格納されている反復子で直接実行されます。ただし、`operator*` の結果は、`value_type&&` に暗黙的にキャストされ、右辺値参照が作成されます。

`move_iterator` は、ラップされた反復子で定義されていない操作が可能である場合があります。 これらの操作は使用しないでください。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[move_iterator](#move_iterator)|`move_iterator` 型のオブジェクトのコンストラクター。|

### <a name="typedefs"></a>Typedefs

|型名|説明|
|-|-|
|[iterator_type](#iterator_type)|テンプレート パラメーター `RandomIterator` のシノニム。|
|[iterator_category](#iterator_category)|同じ名前の長い `typename` 式のシノニム、`iterator_category` は反復子の汎用機能を識別します。|
|[value_type](#value_type)|同じ名前の長い `typename` 式のシノニム、`value_type` は反復子要素の型を表します。|
|[difference_type](#difference_type)|同じ名前の長い `typename` 式のシノニム、`difference_type` は要素の差分値を表すために必要な整数型を表します。|
|[pointer](#pointer)|テンプレート パラメーター `RandomIterator` のシノニム。|
|[reference](#reference)|`rvalue` 参照 `value_type&&` のシノニム。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[base](#base)|このメンバー関数は、この `move_iterator` によってラップされた、格納されている反復子を返します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[move_iterator::operator*](#op_star)|`(reference)*base().` を返します。|
|[move_iterator::operator++](#op_add_add)|格納されている反復子をインクリメントします。 実際の動作は、前置インクリメント操作であるか、後置インクリメント操作であるかによって異なります。|
|[move_iterator::operator--](#operator--)|格納されている反復子をデクリメントします。 実際の動作は、前置インクリメント操作であるか、後置インクリメント操作であるかによって異なります。|
|[move_iterator::operator-&gt;](#op_arrow)|`&**this` を返します。|
|[move_iterator::operator-](#operator-)|最初に現在位置から右側の値を減算することによって `move_iterator(*this) -=` を返します。|
|[move_iterator::operator[]](#op_at)|`(reference)*(*this + off)` を返します。 現在のベースからのオフセットを指定し、その位置の値を取得できます。|
|[move_iterator::operator+](#op_add)|`move_iterator(*this) +=` に値を返します。 ベースにオフセットを加算し、その位置の値を取得できます。|
|[move_iterator::operator+=](#op_add_eq)|右辺値を格納されている反復子に加算し、`*this` を返します。|
|[move_iterator::operator-=](#operator-_eq)|右辺値を格納されている反復子から減算し、`*this` を返します。|

## <a name="requirements"></a>要件

**ヘッダー:** \<iterator>

**名前空間:** std

## <a name="base"></a>  move_iterator::base

この `move_iterator` の格納されている反復子を返します。

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>コメント

このメンバー関数は、格納されている反復子を返します。

## <a name="difference_type"></a>  move_iterator::difference_type

型 `difference_type` は、反復子特性 `difference_type` に基づく `move_iterator` `typedef` で、同意語として使用できます。

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>コメント

この型は、反復子特性 `typename iterator_traits<RandomIterator>::pointer` の同意語です。

## <a name="iterator_category"></a>  move_iterator::iterator_category

型 `iterator_category` は、反復子特性 `iterator_category` に基づく `move_iterator` `typedef` で、同意語として使用できます。

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>コメント

この型は、反復子特性 `typename iterator_traits<RandomIterator>::iterator_category` の同意語です。

## <a name="iterator_type"></a>  move_iterator::iterator_type

型 `iterator_type` は、クラス テンプレートの `move_iterator` のテンプレート パラメーター `RandomIterator` に基づいていて、代わりに互いに入れ替えて使用できます。

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>コメント

この型は、テンプレート パラメーター `RandomIterator` のシノニムです。

## <a name="move_iterator"></a>  move_iterator::move_iterator

移動反復子を構築します。 格納されている反復子としてパラメーターを使用します。

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>パラメーター

`right` 格納された反復子として使用する反復子。

### <a name="remarks"></a>コメント

最初のコンストラクターは、格納されている反復子を既定のコンストラクターによって初期化します。 残りのコンストラクターは、格納されている反復子を `base.base()` によって初期化します。

## <a name="op_add_eq"></a>  move_iterator::operator+=

格納された反復子にオフセットを追加し、その格納された反復子が新しい現在位置にある要素を指すようにします。 その後、演算子は新しい現在の要素を移動します。

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>パラメーター

`_Off` 新しい現在位置を決定する現在の位置に追加するオフセット。

### <a name="return-value"></a>戻り値

新しい現在の要素を返します。

### <a name="remarks"></a>コメント

演算子は、格納されている反復子に `_Off` を追加します。 その後、`*this` を返します。

## <a name="move_iterator__operator-_eq"></a>  move_iterator::operator-=

指定された数の前の要素の間で移動します。 この演算子は、格納された反復子からオフセットを減算します。

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>パラメーター

### <a name="remarks"></a>コメント

演算子は `*this += -_Off` を評価します。 その後、`*this` を返します。

## <a name="op_add_add"></a>  move_iterator::operator++

`move_iterator.` に属する格納されている反復子をインクリメントします。現在の要素は後置インクリメント演算子によってアクセスされます。 次の要素は前置インクリメント演算子によってアクセスされます。

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>パラメーター

### <a name="remarks"></a>コメント

最初の (前置インクリメント) 演算子は格納されている反復子をインクリメントします。 その後、`*this` を返します。

2 番目の (後置インクリメント) 演算子は `*this` のコピーを作成し、`++*this` を評価します。 その後、コピーを返します。

## <a name="op_add"></a>  move_iterator::operator+

任意の要素の数だけ前方へ進んだ反復子の位置を返します。

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>パラメーター

### <a name="remarks"></a>コメント

この演算子は、`move_iterator(*this) +=` `_Off` を返します。

## <a name="op_at"></a>  move_iterator::operator[]

`move iterator` の範囲の要素への配列インデックスのアクセスを許可します。

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>パラメーター

### <a name="remarks"></a>コメント

この演算子は `(reference)*(*this + _Off)` を返します。

## <a name="move_iterator__operator--"></a>  move_iterator::operator--

Predecrement と postdecrement メンバー演算子は、格納されている反復子でデクリメントを実行します。

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>パラメーター

### <a name="remarks"></a>コメント

最初のメンバー演算子 (predecrement) は、格納されている反復子をデクリメントします。 その後、`*this` を返します。

2 番目の (postdecrement) 演算子は、`*this` のコピーを作成し、`--*this` を評価します。 その後、コピーを返します。

## <a name="move_iterator__operator-"></a>  move_iterator::operator-

格納されている反復子をデクリメントして、指定された値を返します。

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>パラメーター

### <a name="remarks"></a>コメント

この演算子は `move_iterator(*this) -= _Off` を返します。

## <a name="op_star"></a>  move_iterator::operator*

格納されている反復子を逆参照して値を返します。 これは、`rvalue reference` と同じように動作し、移動代入を実行します。 この演算子は、基本反復子から現在の要素を転送します。 後続の要素は、新しい現在の要素になります。

```cpp
reference operator*() const;
```

### <a name="remarks"></a>コメント

この演算子は `(reference)*base()` を返します。

## <a name="op_arrow"></a>  move_iterator::operator-&gt;

通常の`RandomIterator``operator->` のように、現在の要素に属するフィールドへのアクセスを提供します。

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>コメント

この演算子は `&**this` を返します。

## <a name="pointer"></a>  move_iterator::pointer

型 `pointer` は、`move_iterator` のランダム反復子 `RandomIterator` に基づく `typedef` で、同意語として使用できます。

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>コメント

この型は `RandomIterator` の同意語です。

## <a name="reference"></a>  move_iterator::reference

型 `reference` は、`move_iterator` の `value_type&&` に基づく `typedef` で、`value_type&&` の同義語として使用できます。

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>コメント

この型は、右辺値参照である `value_type&&` のシノニムです。

## <a name="value_type"></a>  move_iterator::value_type

型 `value_type` は、反復子特性 `value_type` に基づく `move_iterator` `typedef` で、同意語として使用できます。

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>コメント

この型は、反復子特性 `typename iterator_traits<RandomIterator>::value_type` の同意語です。

## <a name="see-also"></a>関連項目

[\<iterator>](../standard-library/iterator.md)<br/>
[左辺値と右辺値](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[移動コンストラクターと移動代入演算子 (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)<br/>
