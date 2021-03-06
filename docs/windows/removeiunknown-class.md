---
title: RemoveIUnknown クラス |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
dev_langs:
- C++
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb005bc3cbf411a7d5b5ddbfa44cd6aecf802105
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
---
# <a name="removeiunknown-class"></a>RemoveIUnknown クラス
WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。  
  
## <a name="syntax"></a>構文  
  
```  
template <  
   typename T  
>  
struct RemoveIUnknown;  
  
template <  
   typename T  
>  
class RemoveIUnknown : public T;  
```  
  
#### <a name="parameters"></a>パラメーター  
 `T`  
 クラスです。  
  
## <a name="remarks"></a>コメント  
 等価の型を作成、 `IUnknown`-ベースの型が、非仮想`QueryInterface`、 `AddRef`、および`Release`メンバー関数。  
  
 既定では、COM メソッドを提供仮想`QueryInterface`、 `AddRef`、およびメソッドをリリースします。 ただし、`ComPtr`仮想メソッドのオーバーヘッドは必要ありません。 `RemoveIUnknown` プライベートな非仮想を提供することでそのオーバーヘッドを排除`QueryInterface`、 `AddRef`、および`Release`メソッドです。  
  
## <a name="members"></a>メンバー  
  
### <a name="public-typedefs"></a>パブリック typedef  
  
|名前|説明|  
|----------|-----------------|  
|`ReturnType`|テンプレート パラメーターと同等である型のシノニム`T`が非仮想 IUnknown メンバー。|  
  
## <a name="inheritance-hierarchy"></a>継承階層  
 `T`  
  
 `RemoveIUnknown`  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>関連項目  
 [Microsoft::WRL::Details 名前空間](../windows/microsoft-wrl-details-namespace.md)