---
title: 配列 (C++) の使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c2140dbe786a5d2a2a1b86eca17912e5e06b922
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-arrays-c"></a>配列の使用 (C++)
配列添字演算子 (`[ ]`) を使用すると、配列の個々の要素にアクセスできます。 一次元配列が添字のない式で使用されている場合、配列名は配列の最初の要素へのポインターに評価されます。  
  
```  
// using_arrays.cpp  
int main() {  
   char chArray[10];  
   char *pch = chArray;   // Evaluates to a pointer to the first element.  
   char   ch = chArray[0];   // Evaluates to the value of the first element.  
   ch = chArray[3];   // Evaluates to the value of the fourth element.  
}  
```  
  
 多次元配列を使用すると、式でさまざまな組み合わせを使用できます。  
  
```  
// using_arrays_2.cpp  
// compile with: /EHsc /W1  
#include <iostream>  
using namespace std;  
int main() {  
   double multi[4][4][3];   // Declare the array.  
   double (*p2multi)[3];  
   double (*p1multi);  
  
   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.  
   p2multi = multi[3];               // Make p2multi point to  
                                     // fourth "plane" of multi.  
   p1multi = multi[3][2];            // Make p1multi point to  
                                     // fourth plane, third row  
                                     // of multi.  
}  
```  
  
 このコードでは、`multi` は `double` 型の 3 次元配列です。 `p2multi` ポインターは、サイズが 3 で型が `double` の配列を参照します。 この例では、配列が 1 つ、2 つ、および 3 つの添字と共に使用されています。 `cout` ステートメントのように、すべての添字を指定する方が一般的ですが、`cout` に続くステートメントのように、配列要素の特定のサブセットを選択した方が便利なこともあります。  
  
## <a name="see-also"></a>関連項目  
 [配列](../cpp/arrays-cpp.md)