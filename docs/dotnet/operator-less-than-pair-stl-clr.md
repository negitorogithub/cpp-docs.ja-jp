---
title: 演算子&lt;(組) (STL/CLR) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::pair::operator<
dev_langs:
- C++
helpviewer_keywords:
- operator< member [STL/CLR]
ms.assetid: e7061b29-1289-4ea9-ae69-feea8abbfb25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 615056b8a554119a9be1cf49865af66f04db02c7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="operatorlt-pair-stlclr"></a>演算子&lt;(組) (STL/CLR)
ペアの比較よりも小さいです。  
  
## <a name="syntax"></a>構文  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>パラメーター  
 左へ  
 比較する左のペア。  
  
 右  
 比較する右のペア。  
  
## <a name="remarks"></a>コメント  
 演算子関数を返します`left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`です。 テストするために使用するかどうか`left`が順序付け、前に`right`とき要素によって比較対象の要素では 2 つのペア。  
  
## <a name="example"></a>例  
  
```  
// cliext_pair_operator_lt.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] < [x 3] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[x 3] < [x 4] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] < [x 3] is False  
[x 3] < [x 4] is True  
```  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** \<cliext ユーティリティ/>  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>関連項目  
 [ペア (STL/CLR)](../dotnet/pair-stl-clr.md)   
 [演算子 = = (組) (STL/CLR)](../dotnet/operator-equality-pair-stl-clr.md)   
 [operator! = (組) (STL/CLR)](../dotnet/operator-inequality-pair-stl-clr.md)   
 [operator > = (組) (STL/CLR)](../dotnet/operator-greater-or-equal-pair-stl-clr.md)   
 [operator > (組) (STL/CLR)](../dotnet/operator-greater-than-pair-stl-clr.md)   
 [operator<= (pair) (STL/CLR)](../dotnet/operator-less-or-equal-pair-stl-clr.md)