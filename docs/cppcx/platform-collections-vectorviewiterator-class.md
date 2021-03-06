---
title: Platform::Collections::VectorViewIterator クラス |Microsoft ドキュメント
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
dev_langs:
- C++
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e01a6235ccd898e9ae732c89b9f9885db35151cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator クラス
Windows ランタイムの派生オブジェクトの標準テンプレート ライブラリ反復子を提供`IVectorView`インターフェイスです。  
  
 `ViewVectorIterator` は、 `VectorProxy<T>`型の要素を格納するプロキシ反復子です。 ただし、プロキシ オブジェクトは、ユーザー コードにはほとんどは表示されません。 詳細については、「 [Collections (C++/CX) (コレクション (C++/CX))](../cppcx/collections-c-cx.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
template <typename T>  
class VectorViewIterator;  
```  
  
#### <a name="parameters"></a>パラメーター  
 `T`  
 VectorViewIterator テンプレート クラスの型名。  
  
### <a name="members"></a>メンバー  
  
### <a name="public-typedefs"></a>パブリック typedef  
  
|名前|説明|  
|----------|-----------------|  
|`difference_type`|ポインターの相違点 (ptrdiff_t)。|  
|`iterator_category`|ランダム アクセス反復子 (::std::random_access_iterator_tag) のカテゴリ。|  
|`pointer`|VectorViewIterator の実装に必要な内部型へのポインター。|  
|`reference`|VectorViewIterator の実装に必要な内部型への参照。|  
|`value_type`|`T` 型名。|  
  
### <a name="public-constructors"></a>パブリック コンストラクター  
  
|名前|説明|  
|----------|-----------------|  
|[VectorViewIterator::VectorViewIterator](#ctor)|VectorViewIterator クラスの新しいインスタンスを初期化します。|  
  
### <a name="public-operators"></a>パブリック演算子  
  
|名前|説明|  
|----------|-----------------|  
|[VectorViewIterator::operator- 演算子](#operator-minus)|現在の反復子から指定した数の要素を減算して新しい反復子を生成するか、現在の反復子から指定した反復子を減算して反復子間の要素数を生成します。|  
|[VectorViewIterator::operator-- 演算子](#operator-decrement)|現在の VectorViewIterator をデクリメントします。|  
|[VectorViewIterator::operator!= 演算子](#operator-inequality)|現在の VectorViewIterator が、指定された VectorViewIterator と等しくないかどうかを示します。|  
|[VectorViewIterator::operator* 演算子](#operator-dereference)|現在の VectorViewIterator により指定された要素への参照を取得します。|  
|[Vectorviewiterator::operator\[\]](#operator-at)|現在の VectorViewIterator から指定数だけ転置された要素への参照を取得します。|  
|[VectorViewIterator::operator+ 演算子](#operator-plus)|指定された VectorViewIterator から指定された転置にある要素を参照する VectorViewIterator を返します。|  
|[VectorViewIterator::operator++ 演算子](#operator-increment)|現在の VectorViewIterator をインクリメントします。|  
|[VectorViewIterator::operator+= 演算子](#operator-plus-assign)|指定された転置数だけ現在の VectorViewIterator をインクリメントします。|  
|[VectorViewIterator::operator< 演算子](#operator-less-than)|現在の VectorViewIterator が、指定された VectorViewIterator より小さいかどうかを示します。|  
|[Vectorviewiterator::operator\<= 演算子](#operator-less-than-or-equals)|現在の VectorViewIterator が、指定された VectorViewIterator 以下であるかどうかを示します。|  
|[VectorViewIterator::operator-= 演算子](#operator-minus-assign)|現在の VectorViewIterator を、指定されたディスプレイスメントだけデクリメントします。|  
|[VectorViewIterator::operator== 演算子](#operator-equality)|現在の VectorViewIterator が、指定された VectorViewIterator と等しいかどうかを示します。|  
|[VectorViewIterator::operator> 演算子](#operator-greater-than)|現在の VectorViewIterator が、指定された VectorViewIterator より大きいかどうかを示します。|  
|[VectorViewIterator::operator-> 演算子](#operator-arrow)|現在の VectorViewIterator により参照される要素のアドレスを取得します。|  
|[VectorViewIterator::operator>= 演算子](#operator-greater-than-or-equals)|現在の VectorViewIterator が、指定された VectorViewIterator 以上であるかどうかを示します。|  
  
## <a name="inheritance-hierarchy"></a>継承階層  
 `VectorViewIterator`  
  
### <a name="requirements"></a>要件  
 **ヘッダー:** collection.h  
  
 **名前空間:** Platform::Collections  

## <a name="operator-arrow"></a>  Vectorviewiterator::operator-&gt;演算子
現在の VectorViewIterator により参照される要素のアドレスを取得します。  
  
### <a name="syntax"></a>構文  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
### <a name="return-value"></a>戻り値  
 現在の VectorViewIterator により参照される要素の値。  
  
 戻り値の型は、この演算子の実装に必要な、指定されていない内部型です。  
  


## <a name="operator-decrement"></a>  Vectorviewiterator::operator - 演算子
現在の VectorViewIterator をデクリメントします。  
  
### <a name="syntax"></a>構文  
  
```  
VectorViewIterator& operator--();  
VectorViewIterator operator--(int);  
```  
  
### <a name="return-value"></a>戻り値  
 最初の構文は、現在の VectorViewIterator をデクリメントしてから返します。 2 番目の構文は、現在の VectorViewIterator のコピーを返してから、現在の VectorViewIterator をデクリメントします。  
  
### <a name="remarks"></a>コメント  
 最初の VectorViewIterator 構文は、現在の VectorViewIterator の前置デクリメントを実行します。  
  
 2 番目の構文は、現在の VectorViewIterator の後置デクリメントを実行します。 `int` 2 番目の構文の型が後置デクリメント演算、実際の整数オペランドではないことを示します。  
  


## <a name="operator-dereference"></a>  Vectorviewiterator::operator * 演算子
現在の VectorViewIterator により指定された要素への参照を取得します。  
  
### <a name="syntax"></a>構文  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>戻り値  
 現在の VectorViewIterator により指定された要素。  
  


## <a name="operator-equality"></a>  Vectorviewiterator::operator = = 演算子
現在の VectorViewIterator が、指定された VectorViewIterator と等しいかどうかを示します。  
  
### <a name="syntax"></a>構文  
  
```  
bool operator==(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>パラメーター  
 `other`  
 別の VectorViewIterator。  
  
### <a name="return-value"></a>戻り値  
 `true` 現在の VectorViewIterator と等しい場合`other`、それ以外の`false`します。  
  


## <a name="operator-greater-than"></a>  Vectorviewiterator::operator&gt;演算子
現在の VectorViewIterator が、指定された VectorViewIterator より大きいかどうかを示します。  
  
### <a name="syntax"></a>構文  
  
```  
  
bool operator>(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>パラメーター  
 `other`  
 別の VectorViewIterator。  
  
### <a name="return-value"></a>戻り値  
 現在の VectorViewIterator が `true` より大きい場合は `other`。それ以外の場合は `false`。  
  


## <a name="operator-greater-than-or-equals"></a>  Vectorviewiterator::operator&gt;= 演算子
現在の VectorViewIterator が、指定された VectorViewIterator 以上であるかどうかを示します。  
  
### <a name="syntax"></a>構文  
  
```  
  
bool operator>=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>パラメーター  
 `other`  
 別の VectorViewIterator。  
  
### <a name="return-value"></a>戻り値  
 現在の VectorViewIterator が `true` 以上の場合は `other`。それ以外の場合は `false`。  
  


## <a name="operator-increment"></a>  Vectorviewiterator::operator++ 演算子
現在の VectorViewIterator をインクリメントします。  
  
### <a name="syntax"></a>構文  
  
```  
  
VectorViewIterator& operator++();  
VectorViewIterator operator++(int);  
```  
  
### <a name="return-value"></a>戻り値  
 最初の構文は、現在の VectorViewIterator をインクリメントしてから返します。 2 番目の構文は、現在の VectorViewIterator のコピーを返し、現在の VectorViewIterator をインクリメントします。  
  
### <a name="remarks"></a>コメント  
 最初の VectorViewIterator 構文は、現在の VectorViewIterator の前置インクリメントを実行します。  
  
 2 番目の構文は、現在の VectorViewIterator の後置インクリメントを実行します。 2 つ目の構文の `int` 型は、実際の整数オペランドではなく後置インクリメント演算を示します。  
  


## <a name="operator-inequality"></a>  Vectorviewiterator::operator! = 演算子
現在の VectorViewIterator が、指定された VectorViewIterator と等しくないかどうかを示します。  
  
### <a name="syntax"></a>構文  
  
```  
bool operator!=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>パラメーター  
 `other`  
 別の VectorViewIterator。  
  
### <a name="return-value"></a>戻り値  
 `true` 現在の VectorViewIterator と等しくない場合`other`、それ以外の`false`します。  
  


## <a name="operator-less-than"></a>  Vectorviewiterator::operator&lt;演算子
現在の VectorIterator が、指定された VectorIterator より小さいかどうかを示します。  
  
### <a name="syntax"></a>構文  
  
```  
bool operator<(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>パラメーター  
 `other`  
 別の VectorIterator。  
  
### <a name="return-value"></a>戻り値  
 現在の VectorIterator が `true` より小さい場合は `other`。それ以外の場合は `false`。  
  


## <a name="operator-less-than-or-equals"></a>  Vectorviewiterator::operator&lt;= 演算子
現在の VectorIterator が、指定された VectorIterator 以下かどうかを示します。  
  
### <a name="syntax"></a>構文  
  
```  
  
bool operator<=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>パラメーター  
 `other`  
 別の VectorIterator。  
  
### <a name="return-value"></a>戻り値  
 `true` かどうか、現在の VectorIterator より小さいかに等しい`other`、それ以外の`false`します。  
  


## <a name="operator-minus"></a>  Vectorviewiterator::operator-演算子
現在の反復子から指定した数の要素を減算して新しい反復子を生成するか、現在の反復子から指定した反復子を減算して反復子間の要素数を生成します。  
  
### <a name="syntax"></a>構文  
  
```  
  
VectorViewIterator operator-(difference_type n) const;  
  
difference_type operator-(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>パラメーター  
 `n`  
 要素の数。  
  
 `other`  
 別の VectorViewIterator。  
  
### <a name="return-value"></a>戻り値  
 最初の演算子構文は、現在の VectorViewIterator より `n` 要素少ない VectorViewIterator オブジェクトを返します。 2 番目の演算子構文は、現在の VectorViewIterator と `other` VectorViewIterator の間の要素の数を返します。  
  


## <a name="operator-plus-equals"></a>  Vectorviewiterator::operator + = 演算子
指定された転置数だけ現在の VectorViewIterator をインクリメントします。  
  
### <a name="syntax"></a>構文  
  
```  
VectorViewIterator& operator+=(difference_type n);  
```  
  
### <a name="parameters"></a>パラメーター  
 `n`  
 整数の転置。  
  
### <a name="return-value"></a>戻り値  
 更新された VectorViewIterator。  
  


## <a name="operator-plus"></a>  Vectorviewiterator::operator + 演算子
指定された VectorViewIterator から指定された転置にある要素を参照する VectorViewIterator を返します。  
  
### <a name="syntax"></a>構文  
  
```  
  
VectorViewIterator operator+(difference_type n) const;  
  
template <typename T>   
inline VectorViewIterator<T> operator+  
   (ptrdiff_t n,   
   const VectorViewIterator<T>& i);  
  
```  
  
### <a name="parameters"></a>パラメーター  
 `T`  
 2 番目の構文では、VectorViewIterator の型名。  
  
 `n`  
 整数のディスプレイスメント。  
  
 `i`  
 2 番目の構文では、VectorViewIterator。  
  
### <a name="return-value"></a>戻り値  
 最初の構文では、現在の VectorViewIterator から指定された転置にある要素を参照する VectorViewIterator。  
  
 2 番目の構文、パラメーターの先頭から指定された転置にある要素を参照する VectorViewIterator で`i`です。  
  


## <a name="operator-minus-assign"></a>  Vectorviewiterator::operator-= 演算子
指定されたディスプレイスメントだけ現在の VectorIterator をデクリメントします。  
  
### <a name="syntax"></a>構文  
  
```  
VectorViewIterator& operator-=(difference_type n);  
```  
  
### <a name="parameters"></a>パラメーター  
 `n`  
 整数のディスプレイスメント。  
  
### <a name="return-value"></a>戻り値  
 更新された VectorIterator。  
  


## <a name="operator-at"></a>  Vectorviewiterator::operator\[\]
現在の VectorViewIterator から指定数だけ転置された要素への参照を取得します。  
  
### <a name="syntax"></a>構文  
  
```  
reference operator[](difference_type n) const;  
```  
  
### <a name="parameters"></a>パラメーター  
 `n`  
 整数のディスプレイスメント。  
  
### <a name="return-value"></a>戻り値  
 現在の VectorViewIterator から `n` 要素だけ転置された要素。  
  


## <a name="ctor"></a>  Vectorviewiterator::vectorviewiterator コンス トラクター
VectorViewIterator クラスの新しいインスタンスを初期化します。  
  
### <a name="syntax"></a>構文  
  
```  
  
VectorViewIterator();  
  
explicit VectorViewIterator(  
   Windows::Foundation::Collections::IVectorView<T>^ v  
);  
```  
  
### <a name="parameters"></a>パラメーター  
 `v`  
 IVectorView\<T > オブジェクト。  
  
### <a name="remarks"></a>コメント  
 最初の構文例は既定のコンストラクターです。 2 番目の構文例は、IVectorView から VectorViewIterator を構築するために使用される明示的なコンス トラクター\<T > オブジェクト。  
  

  
## <a name="see-also"></a>関連項目  
 [プラットフォーム Namespace](platform-namespace-c-cx.md)