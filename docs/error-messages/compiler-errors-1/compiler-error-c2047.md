---
title: コンパイラ エラー C2047 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2047
dev_langs:
- C++
helpviewer_keywords:
- C2047
ms.assetid: 686a5a81-3857-4753-84a0-5c2e7149cbee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16aed5b8100a3591fcdfbb4451a76db51a5f3b4d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2047"></a>コンパイラ エラー C2047
'default' が正しくありません。  
  
 キーワード `default` は `switch` ステートメントでのみ使用できます。  
  
 次の例では C2047 が生成されます。  
  
```  
// C2047.cpp  
int main() {  
   int i = 0;  
   default:   // C2047  
   switch(i) {  
      case 0:  
      break;  
   }  
}  
```  
  
 考えられる解決方法:  
  
```  
// C2047b.cpp  
int main() {  
   int i = 0;  
   switch(i) {  
      case 0:  
      break;  
      default:  
      break;  
   }  
}  
```