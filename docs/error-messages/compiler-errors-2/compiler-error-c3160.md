---
title: コンパイラ エラー C3160 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3160
dev_langs:
- C++
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 670dd386be82b4356262cb59442d36fb1d6f646b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3160"></a>コンパイラ エラー C3160
'pointer': マネージ クラスまたは WinRT クラスのデータ メンバーにはこの型を指定できません。  
  
 内部のガベージ コレクション ポインターは、マネージ クラスまたは WinRT クラスの内部を指す場合があります。 オブジェクト全体のポインターよりも遅く、ガベージ コレクターによる特別な処理を必要とするため、クラスのメンバーとして内部のマネージ ポインターを宣言することはできません。  
  
 次の例では C3160 が生成されます。  
  
```  
// C3160.cpp  
// compile with: /clr  
ref struct A {  
   // cannot create interior pointers inside a class  
   interior_ptr<int> pg;   // C3160  
   int g;   // OK  
   int* pg2;   // OK  
};  
  
int main() {  
   interior_ptr<int> pg2;   // OK  
}  
```  
