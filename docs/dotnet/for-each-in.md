---
title: ごとで |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
dev_langs:
- C++
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6ab5f7309da1a037f7066d44815cafc934b162cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="for-each-in"></a>for each、in
配列またはコレクションを反復処理します。 この非標準のキーワードは、C++/CLI プロジェクトと C++ ネイティブ プロジェクトの両方で使用できます。 ただし、これを使用することはお勧めしません。 標準的な使用を検討して[ステートメント (C++) の範囲に基づく](../cpp/range-based-for-statement-cpp.md)代わりにします。  
  
## <a name="all-runtimes"></a>すべてのランタイム  
 **構文**  
  
```  
  
      for each (typeidentifierinexpression) {  
   statements  
}  
  
```  
  
 **パラメーター**  
  
 `type`  
 `identifier` の型。  
  
 `identifier`  
 コレクション要素を表す繰り返し変数。  ときに`identifier`は、[参照演算子の追跡](../windows/tracking-reference-operator-cpp-component-extensions.md)要素を変更することができます。  
  
 `expression`  
 配列式またはコレクション。 コレクション要素は、コンパイラが `identifier` 型に変換できるようにする必要があります。  
  
 `statements`  
 実行する 1 つ以上のステートメントを指定します。  
  
 **解説**  
  
 コレクションを反復処理するために、`for each` ステートメントを使用します。 コレクション内の要素を変更することはできますが、要素を追加または削除することはできません。  
  
 *ステートメント*配列またはコレクションの各要素に対して実行されます。 コレクション内の全要素に対する繰り返しが完了すると、制御は、`for each` ブロックに続くステートメントに移動します。  
  
 `for each` および`in`は[状況依存のキーワード](../windows/context-sensitive-keywords-cpp-component-extensions.md)です。  
  
 詳細情報  
  
-   [for each を使用した C++ 標準ライブラリ コレクションの反復処理](../dotnet/iterating-over-stl-collection-by-using-for-each.md)  
  
-   [方法: for each を使用して配列を反復処理する](../dotnet/how-to-iterate-over-arrays-with-for-each.md)  
  
-   [方法: for each を使用してジェネリック コレクションを反復処理する](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)  
  
-   [方法: for each を使用してユーサー定義のコレクションを反復処理する](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)  
  
## <a name="windows-runtime"></a>Windows ランタイム  
  
### <a name="requirements"></a>要件  
 コンパイラ オプション: **/ZW**  
  
### <a name="example"></a>例  
 この例では、`for each` を使用して文字列を反復処理する方法を示します。  
  
```  
// for_each_string1.cpp  
// compile with: /ZW  
#include <stdio.h>  
using namespace Platform;  
  
ref struct MyClass {  
   property String^ MyStringProperty;  
};  
  
int main() {  
   String^ MyString = ref new String("abcd");  
  
   for each ( char c in MyString )  
      wprintf("%c", c);  
  
   wprintf("/n");  
  
   MyClass^ x = ref new MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( char c in x->MyStringProperty )  
      wprintf("%c", c);  
}  
```  
  
 **出力**  
  
```Output  
abcd  
  
Testing  
```  
  
## <a name="common-language-runtime"></a>共通言語ランタイム 
 **解説**  
  
 CLR の構文は同じ、**すべてのランタイム**構文を次のようを除きます。  
  
 *式*  
 マネージ配列式またはコレクション。 コレクション要素は、コンパイラがからに変換できるようにする必要があります<xref:System.Object>を*識別子*型です。  
  
 *式*を実装する型に評価される<xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、または、定義された型、`GetEnumerator`を実装するメソッドの型を返すか<xref:System.Collections.IEnumerator>すべてで定義されているメソッドの宣言または`IEnumerator`.  
  
### <a name="requirements"></a>要件  
 コンパイラ オプション: **/clr**  
  
### <a name="example"></a>例  
 この例では、`for each` を使用して文字列を反復処理する方法を示します。  
  
```  
// for_each_string2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct MyClass {  
   property String ^ MyStringProperty;  
};  
  
int main() {  
   String ^ MyString = gcnew String("abcd");  
  
   for each ( Char c in MyString )  
      Console::Write(c);  
  
   Console::WriteLine();  
  
   MyClass ^ x = gcnew MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( Char c in x->MyStringProperty )  
      Console::Write(c);  
}  
```  
  
 **出力**  
  
```Output  
abcd  
  
Testing   
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム プラットフォームのコンポーネントの拡張機能](../windows/component-extensions-for-runtime-platforms.md)