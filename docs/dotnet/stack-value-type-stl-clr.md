---
title: stack::value_type (STL/CLR) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: 867ff1a7-c91c-4168-9b85-21fd0dcf4806
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: af40e4dfdc5f0ec547c3aa22b94d24eda35008b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="stackvaluetype-stlclr"></a>stack::value_type (STL/CLR)
要素の型。  
  
## <a name="syntax"></a>構文  
  
```  
typedef Value value_type;  
```  
  
## <a name="remarks"></a>コメント  
 この型は、テンプレート パラメーター `Value` のシノニムです。  
  
## <a name="example"></a>例  
  
```  
// cliext_stack_value_type.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Mystack::value_type val = c1.top();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** \<cliext/stack >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>関連項目  
 [スタック (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::const_reference (STL/CLR)](../dotnet/stack-const-reference-stl-clr.md)   
 [stack::reference (STL/CLR)](../dotnet/stack-reference-stl-clr.md)