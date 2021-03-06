---
title: 名前空間 (C++) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/30/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- namespace_CPP
- using_CPP
dev_langs:
- C++
helpviewer_keywords:
- namespaces [C++], C++
- namespaces [C++]
- namespaces [C++], global
- global namespace
- Visual C++, namespaces
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aac72a23e50ca3bc6d5b737d533bd11a40ed9da3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="namespaces-c"></a>名前空間 (C++)
名前空間は、その内部にある識別子 (型、関数、変数などの名前) のスコープを定める宣言領域です。 名前空間は、コードを論理グループにまとめるため、およびコード ベースに複数のライブラリが含まれる場合に特に発生する名前の競合を回避するために使用されます。 名前空間スコープのすべての識別子は互いどうしを修飾なしで参照できます。 名前空間の外部識別子は、たとえば、各識別子の完全修飾名を使用してメンバーにアクセスできます`std::vector<std::string> vec;`、または else によって、[宣言を使用して](../cpp/using-declaration.md)、単一の識別子の (`using std::string`)、または、 [ディレクティブを使用して](../cpp/namespaces-cpp.md#using_directives)、名前空間内のすべての識別子 (`using namespace std;`)。 ヘッダー ファイル内のコードは、常に完全修飾された名前空間の名前を使用する必要があります。  
  
 次の例は、名前空間宣言とともに、名前空間の外部のコードがメンバーにアクセスできる 3 つの方法を示しています。  
  
```cpp  
namespace ContosoData  
{      
    class ObjectManager   
    {  
    public:  
        void DoSomething() {}  
    };  
    void Func(ObjectManager) {}  
}  
```  
  
 完全修飾名の使用:  
  
```cpp  
ContosoData::ObjectManager mgr;  
mgr.DoSomething();  
ContosoData::Func(mgr);  
```  
  
 using 宣言を使用すると、1 つの識別子をスコープに挿入できます。  
  
```cpp  
using ContosoData::ObjectManager;  
ObjectManager mgr;  
mgr.DoSomething();  
  
```  
  
 using ディレクティブを使用すると、名前空間にあるすべてのものをスコープに挿入できます。  
  
```cpp  
using namespace ContosoData;
  
ObjectManager mgr;  
mgr.DoSomething();  
Func(mgr);  
  
```  
  
## <a id="using_directives"></a> ディレクティブを使用します。  
 `using`ディレクティブ内のすべての名を使用して、**名前空間**なしで使用する、*名前空間名*で明示的な修飾子として。 使用して、使用して、名前空間に複数の異なる識別子を使用している場合、実装ファイル (つまり *.cpp) でディレクティブ使用して、検討し、1 つまたは 2 つの識別子だけを使用する場合にのみ取り込むこれらの識別子のスコープとすべての識別子、名前空間で宣言します。 ローカル変数に名前空間変数と同じ名前が付いている場合、名前空間変数が不可視になります。 グローバル変数と同じ名前の名前空間変数を使用するとエラーになります。  
  
> [!NOTE]
>  using ディレクティブは、.cpp ファイルの冒頭に配置するか (ファイル スコープ)、クラス内または関数定義内に配置できます。  
>   
>  通常は、using ディレクティブをヘッダー ファイル (*.h) に配置することは避けてください。このヘッダーをインクルードするすべてのファイルが、名前空間にあるすべてのものをスコープに挿入して、デバッグが非常に困難な名前の隠蔽の問題や名前の競合の問題を引き起こすことがあるためです。 ヘッダー ファイルには常に完全修飾名を使用してください。 完全修飾名が長すぎる場合は、名前空間のエイリアスを使用して短縮します。 (以下を参照してください。)  
  
## <a name="declaring-namespaces-and-namespace-members"></a>名前空間と名前空間のメンバーの宣言  
 一般的に、名前空間はヘッダー ファイル内で宣言します。 関数の実装が別のファイルにある場合は、次の例のように関数名を修飾します。  
  
```cpp  
//contosoData.h   
#pragma once  
namespace ContosoDataServer  
{  
    void Foo();  
    int Bar();  
  
}  
```  
  
 配置する場合でも、contosodata.cpp での関数の実装は、完全修飾名を使用する必要があります、`using`ファイルの上部にあるディレクティブ。  
  
```cpp  
#include "contosodata.h"  
using namespace ContosoDataServer;   
  
void ContosoDataServer::Foo() // use fully-qualified name here  
{  
   // no qualification needed for Bar()  
   Bar();   
}  
  
int ContosoDataServer::Bar(){return 0;}  
```  
  
 名前空間は、1 つのファイルにある複数のブロック、および複数のファイルで宣言できます。 コンパイラは、プリプロセス時にパーツを結合します。結果として生成される名前空間には、すべてのパーツで宣言されるすべてのメンバーが含まれます。 この一例が、標準ライブラリの各ヘッダー ファイルで宣言されている std 名前空間です。  
  
 定義した名前の明示的な修飾で宣言されている名前空間の外部名前空間のメンバーを定義できます。 ただし、定義は、宣言の名前空間を囲う名前空間内で、宣言の位置の後に記述する必要があります。 例えば:  
  
```cpp  
// defining_namespace_members.cpp  
// C2039 expected  
namespace V {  
        void f();  
    }  
  
    void V::f() { }        // ok  
    void V::g() { }        // C2039, g() is not yet a member of V  
  
    namespace V {  
        void g();  
    }  
}  
```  
  
 このエラーは、名前空間のメンバーが複数のヘッダー ファイルで宣言されており、かつこれらのヘッダーを正しい順序でインクルードしなかった場合に発生します。  
  
## <a name="the-global-namespace"></a>グローバル名前空間  
 識別子は、明示的な名前空間で宣言されていない場合は、暗黙のグローバル名前空間の一部になります。 可能であれば、エントリ ポイントを除く、グローバル スコープで宣言しないようにしようとするは一般的に、 [main 関数](../c-language/main-function-and-program-execution.md)、グローバル名前空間に配置に必要です。 グローバル識別子を明示的に修飾するには、`::SomeFunction(x);` のように、名前のないスコープ解決演算子を使用します。 これにより、識別子は他のあらゆる名前空間にある同じ名前のすべてのものから区別され、コードも他のユーザーに理解しやすいものになります。  
  
## <a name="the-std-namespace"></a>std 名前空間  
 すべての C++ 標準ライブラリの型および関数がで宣言されている、`std`名前空間または名前空間内にネスト`std`です。  
  
## <a name="nested-namespaces"></a>入れ子になった名前空間  
 名前空間は入れ子にすることができます。 次の例に示すように、入れ子になった通常の名前空間には、その親メンバーへの非修飾のアクセス権がありますが、親メンバーには (インラインとして宣言されていない限り) 入れ子になった名前空間への非修飾のアクセス権がありません。  
  
```cpp  
namespace ContosoDataServer  
{  
    void Foo();   
  
    namespace Details  
    {  
        int CountImpl;  
        void Ban() { return Foo(); }  
    }  
  
    int Bar(){...};  
    int Baz(int i) { return Details::CountImpl; }      
  
}  
```  
  
 入れ子になった通常の名前空間は、親の名前空間のパブリック インターフェイスの一部ではない内部実装の詳細をカプセル化するために使用できます。  
  
## <a name="inline-namespaces-c-11"></a>インライン名前空間 (C++ 11)  
 入れ子になった通常の名前空間とは対照的に、インライン名前空間のメンバーは親の名前空間のメンバーとして扱われます。 この特性のおかげで、オーバーロードされた関数に対する引数依存の参照を、親の名前空間と入れ子のインライン名前空間にオーバーロードを持つ関数に対して使用できます。 また、インライン名前空間で宣言されているテンプレートの特殊化を親の名前空間で宣言することもできます。 次の例は、外部のコードを既定でインライン名前空間にバインドする方法を示しています。  
  
```cpp  
//Header.h  
#include <string>  
  
namespace Test  
{  
    namespace old_ns  
    {  
        std::string Func() { return std::string("Hello from old"); }  
    }  
  
    inline namespace new_ns  
    {  
        std::string Func() { return std::string("Hello from new"); }  
    }  
}  
  
#include "header.h"  
#include <string>  
#include <iostream>  
  
int main()  
{  
    using namespace Test;  
    using namespace std;  
  
    string s = Func();  
    std::cout << s << std::endl; // "Hello from new"  
    return 0;  
}  
```  
  
 次の例は、インライン名前空間で宣言されているテンプレートの特殊化を親で宣言する方法を示しています。  
  
```cpp  
namespace Parent  
{  
    inline namespace new_ns  
    {  
         template <typename T>  
         struct C  
         {  
             T member;  
         };  
    }  
     template<>  
     class C<int> {};  
}  
  
```  
  
 ライブラリのパブリック インターフェイスに対する変更を管理するためのバージョン管理のメカニズムとして、インライン名前空間を使用することができます。 たとえば、単一の親名前空間を作成し、インターフェイスの各バージョンを、親の中に入れ子になっている、それぞれ独自の名前空間にカプセル化することができます。 最新または最優先のバージョンを保持する名前空間をインラインとして修飾することで、これを親の名前空間の直接のメンバーであるかのように公開できます。 Parent::Class を呼び出すクライアント コードは、新しいコードに自動的にバインドされます。 古いバージョンを使用するクライアントは、そのコードを持つ入れ子になった名前空間への完全修飾パスを使用すれば、引き続き古いバージョンにアクセスできます。  
  
 inline キーワードは、コンパイル単位内の名前空間の最初の宣言に適用する必要があります。  
  
 次の例は、あるインターフェイスの 2 つのバージョンを示しています。それぞれ入れ子になった名前空間に置かれています。 `v_20` 名前空間には、`v_10` インターフェイスからの変更があり、インラインとしてマークされます。 新しいライブラリを使用し、`Contoso::Funcs::Add` を呼び出すクライアント コードは、v_20 バージョンを呼び出します。 `Contoso::Funcs::Divide` を呼び出そうとするコードは、コンパイル時エラーになります。 その関数が実際に必要な場合は、明示的に `Contoso::v_10::Funcs::Divide` を呼び出して引き続き `v_10` バージョンにアクセスすることができます。  
  
```cpp  
namespace Contoso  
{  
    namespace v_10  
    {  
        template <typename T>  
        class Funcs  
        {  
        public:  
            Funcs(void);  
            T Add(T a, T b);  
            T Subtract(T a, T b);  
            T Multiply(T a, T b);  
            T Divide(T a, T b);  
        };  
    }  
  
    inline namespace v_20  
    {  
        template <typename T>  
        class Funcs  
        {  
        public:  
            Funcs(void);  
            T Add(T a, T b);  
            T Subtract(T a, T b);  
            T Multiply(T a, T b);  
            std::vector<double> Log(double);  
            T Accumulate(std::vector<T> nums);  
      };  
    }  
}  
  
```  
  
## <a id="namespace_aliases"></a> Namespace エイリアス  
 名前空間の名前は一意である必要があります。つまり、多くの場合、短くなりすぎないようにする必要があります。 名前が長くてコードが読みにくい場合、または using ディレクティブを使用できないヘッダー ファイルに入力するのが面倒な場合は、実際の名前の省略形として機能する名前空間のエイリアスを作成することができます。 例えば:  
  
```cpp  
namespace a_very_long_namespace_name { class Foo {}; }  
namespace AVLNN = a_very_long_namespace_name;  
void Bar(AVLNN::Foo foo){ }  
  
```  
  
## <a name="anonymous-or-unnamed-namespaces"></a>匿名または名前のない名前空間  
 名前を付けないで明示的な名前空間を作成することができます。  
  
```cpp  
namespace  
{  
    int MyFunc(){}  
}  
```  
  
 これし、呼ばれ、無名または匿名の名前空間の他のファイルで変数の宣言をコードに非表示にする場合に便利です (つまりは与えられた内部リンケージ) 名前空間を作成する必要はありません。 同じファイル内のすべてのコードは名前のない名前空間の識別子を参照できますが、そのファイルの外 (より厳密に言えば、翻訳単位の外) では、識別子および名前空間自体が不可視になります。  
  
## <a name="see-also"></a>関連項目  
 [宣言と定義](declarations-and-definitions-cpp.md)
