---
title: コンパイラ エラー C3058 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3058
dev_langs:
- C++
helpviewer_keywords:
- C3058
ms.assetid: 669d08c8-0b58-4351-88aa-c6e6e1af481c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 867dbdead4c4268035b5c34a5ef053b959c822a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3058"></a>コンパイラ エラー C3058
'symbol' : シンボルは、'copyin' 句の中で使用される前に 'threadprivate' として宣言されていません  
  
 シンボルは、 [copyin](../../parallel/openmp/reference/threadprivate.md) 句で使用する前に、最初に [threadprivate](../../parallel/openmp/reference/copyin.md) として宣言されている必要があります。  
  
 次の例では C3058 が生成されます。  
  
```  
// C3058.cpp  
// compile with: /openmp  
int x, y, z;  
#pragma omp threadprivate(x, z)  
  
void test() {  
   #pragma omp parallel copyin(x, y)   // C3058  
   {  
   }  
}  
```  
  
 考えられる解決方法:  
  
```  
// C3058b.cpp  
// compile with: /openmp /LD  
int x, y, z;  
#pragma omp threadprivate(x, y)  
  
void test() {  
   #pragma omp parallel copyin(x, y)  
   {  
   }  
}  
```