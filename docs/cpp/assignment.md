---
title: 割り当て |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66fd08215c3849bf487578b28b1824afbec14c52
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="assignment"></a>代入
代入演算子 (**=**) は、厳密には、二項演算子です。 この宣言は他の二項演算子と同じですが、次の例外があります。  
  
-   非静的メンバー関数である必要があります。 非メンバー関数として宣言できる `operator=` はありません。  
  
-   派生クラスにより継承されません。  
  
-   既定の `operator=` 関数は、何も存在しない場合はコンパイラによってクラス型に対して生成できます  (既定値の詳細については`operator=`関数を参照してください[メンバーごとの代入と初期化](http://msdn.microsoft.com/en-us/94048213-8b49-4416-8069-b1b7a6f271f9))。  
  
 次の例では、代入演算子を宣言する方法を示しています。  
  
```  
// assignment.cpp  
class Point  
{  
public:  
   Point &operator=( Point & );  // Right side is the argument.  
   int _x, _y;  
};  
  
// Define assignment operator.  
Point &Point::operator=( Point &ptRHS )  
{  
   _x = ptRHS._x;  
   _y = ptRHS._y;  
  
   return *this;  // Assignment operator returns left side.  
}  
  
int main()  
{  
}  
```  
  
 指定された引数が式の右側にあることに注意してください。 演算子は、代入の完了後に左側の値を返す代入演算子の動作を保持するオブジェクトを返します。 これにより、次のようなステートメントを記述できます。  
  
```  
pt1 = pt2 = pt3;  
```  
  
## <a name="see-also"></a>関連項目  
 [演算子のオーバーロード](../cpp/operator-overloading.md)