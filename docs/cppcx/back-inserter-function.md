---
title: back_inserter 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::back_inserter
dev_langs:
- C++
helpviewer_keywords:
- back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 532b831dfd09a3a1a00637feafabcfd037b05156
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="backinserter-function"></a>back_inserter 関数
指定されたコレクションの末尾に要素を挿入するために使用される反復子を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
template <typename T>
Platform::BackInsertIterator<T>   
    back_inserter(IVector<T>^ v);  
  
template<typename T>  
Platform::BackInsertIterator<T>   
   back_inserter(IObservableVector<T>^ v);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `T`  
 テンプレート型パラメーター。  
  
 `v`  
 基になるコレクションへのアクセスを提供するインターフェイス ポインター。  
  
### <a name="return-value"></a>戻り値  
 反復子。  
  
### <a name="requirements"></a>要件  
 **ヘッダー:** collection.h  
  
 **名前空間:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>関連項目  
 [:Foundation Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)