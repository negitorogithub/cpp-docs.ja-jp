---
title: stack::top_item (STL/CLR) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack::top_item
dev_langs:
- C++
helpviewer_keywords:
- top_item member [STL/CLR]
ms.assetid: 01571acf-4880-44c4-80c4-bd91408a032d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a0faaac744ddd45d9e6b22a2c1390d35401e5e4f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="stacktopitem-stlclr"></a>stack::top_item (STL/CLR)
最後の要素にアクセスします。  
  
## <a name="syntax"></a>構文  
  
```  
property value_type top_item;  
```  
  
## <a name="remarks"></a>コメント  
 プロパティでは、空でない必要があります、被制御シーケンスの最後の要素にアクセスします。 これを使用するには存在することがわかっている場合に、最後の要素を読み書きします。  
  
## <a name="example"></a>例  
  
```  
// cliext_stack_top_item.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top_item = {0}", c1.top_item);   
  
// alter last item and reinspect   
    c1.top_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
top_item = c  
 a b x  
```  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** \<cliext/stack >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>関連項目  
 [スタック (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::top (STL/CLR)](../dotnet/stack-top-stl-clr.md)