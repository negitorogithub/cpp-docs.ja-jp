---
title: 反復子のデバッグのサポート | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- C++ Standard Library, debug iterator support
- iterators, debug iterator support
- iterators, incompatible
- incompatible iterators
- debug iterator support
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9153d5e85540c50e11e096c33c474f1344d3ad2f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="debug-iterator-support"></a>Debug Iterator Support

Visual C++ ランタイム ライブラリは、反復子の不正な使用を検出し、実行時にアサートしてダイアログ ボックスを表示します。 反復子のデバッグのサポートを有効にするには、デバッグ バージョンの C++ 標準ライブラリと C ランタイム ライブラリを使ってプログラムをコンパイルする必要があります。 詳しくは、「[CRT ライブラリの機能](../c-runtime-library/crt-library-features.md)」をご覧ください。 チェックを行う反復子を使う方法については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」をご覧ください。

C++ 標準では、メンバー関数によってコンテナーに対する反復子が無効になる状況が説明されています。 次に 2 つの例を示します。

- コンテナーから要素を消去すると、要素に対する反復子が無効になります。

- プッシュまたは挿入を使って [vector](../standard-library/vector.md) のサイズを大きくすると、`vector` に対する反復子が無効になります。

## <a name="example"></a>例

デバッグ モードで次のサンプル プログラムをコンパイルすると、実行時にアサートして終了します。

```cpp
// iterator_debugging_0.cpp
// compile by using /EHsc /MDd
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v ;

   v.push_back(10);
   v.push_back(15);
   v.push_back(20);

   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

## <a name="example"></a>例

プリプロセッサ マクロ [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) を使って、デバッグ ビルドで反復子デバッグ機能を無効にできます。 このプログラムはアサートしませんが、それでも未定義の動作をトリガーします。

```cpp
// iterator_debugging_1.cpp
// compile by using: /EHsc /MDd
#define _ITERATOR_DEBUG_LEVEL 0
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v ;

   v.push_back(10);
   v.push_back(15);
   v.push_back(20);

   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

```Output
20
-572662307
```

## <a name="example"></a>例

次の例に示すように、初期化する前に反復子を使おうとした場合も、アサートが発生します。

```cpp
// iterator_debugging_2.cpp
// compile by using: /EHsc /MDd
#include <string>
using namespace std;

int main() {
   string::iterator i1, i2;
   if (i1 == i2)
      ;
}
```

## <a name="example"></a>例

次のコード例では、[for_each](../standard-library/algorithm-functions.md#for_each) アルゴリズムに対する 2 つの反復子の間に互換性がないため、アサーションが発生します。 アルゴリズムは、提供された反復子が同じコンテナーを参照しているかどうかを確認します。

```cpp
// iterator_debugging_3.cpp
// compile by using /EHsc /MDd
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
    vector<int> v1;
    vector<int> v2;

    v1.push_back(10);
    v1.push_back(20);

    v2.push_back(10);
    v2.push_back(20);

    // The next line asserts because v1 and v2 are
    // incompatible.
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );
}
```

この例では、ファンクターの代わりにラムダ式 `[] (int& elem) { elem *= 2; }` が使われていることに注意してください。 このようにしてもアサート失敗に影響はありませんが (似たファンクターが同じエラーの原因になります)、ラムダはコンパクトな関数オブジェクト タスクを実行する非常に便利な方法です。 ラムダ式について詳しくは、「[ラムダ式](../cpp/lambda-expressions-in-cpp.md)」をご覧ください。

## <a name="example"></a>例

また、反復子のデバッグのチェックにより、`for` ループで宣言されている反復子変数は、`for` ループのスコープが終了するとスコープ外になります。

```cpp
// iterator_debugging_4.cpp
// compile by using: /EHsc /MDd
#include <vector>
#include <iostream>
int main() {
   std::vector<int> v ;

   v.push_back(10);
   v.push_back(15);
   v.push_back(20);

   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)
      ;   // do nothing
   --i;   // C2065
}
```

## <a name="example"></a>例

反復子のデバッグには重要なデストラクターがあります。 何らかの理由でデストラクターが実行されない場合、アクセス違反とデータの破損が発生する可能性があります。 次の例について考えます。

```cpp
// iterator_debugging_5.cpp
// compile by using: /EHsc /MDd
#include <vector>
struct base {
   // TO FIX: uncomment the next line
   // virtual ~base() {}
};

struct derived : base {
   std::vector<int>::iterator m_iter;
   derived( std::vector<int>::iterator iter ) : m_iter( iter ) {}
   ~derived() {}
};

int main() {
   std::vector<int> vect( 10 );
   base * pb = new derived( vect.begin() );
   delete pb;  // doesn't call ~derived()
   // access violation
}
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリの概要](../standard-library/cpp-standard-library-overview.md)<br/>
