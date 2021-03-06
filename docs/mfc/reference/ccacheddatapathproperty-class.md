---
title: クラスのプロパティ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
dev_langs:
- C++
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29e46f7e65d6c2f9b5c0d29007cd31f660754957
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ccacheddatapathproperty-class"></a>プロパティ クラス
非同期で転送し、メモリ ファイルにキャッシュする OLE コントロール プロパティを実装します。  
  
## <a name="syntax"></a>構文  
  
```  
class CCachedDataPathProperty : public CDataPathProperty  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="public-constructors"></a>パブリック コンストラクター  
  
|名前|説明|  
|----------|-----------------|  
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|`CCachedDataPathProperty` オブジェクトを構築します。|  
  
### <a name="public-data-members"></a>パブリック データ メンバー  
  
|名前|説明|  
|----------|-----------------|  
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile` データをキャッシュするオブジェクト。|  
  
## <a name="remarks"></a>コメント  
 メモリ ファイルはディスクではなく RAM に格納されてし、一時的な高速を転送するため便利です。  
  
 と共に**CAysncMonikerFile**と`CDataPathProperty`、 `CCachedDataPathProperty` OLE コントロールで非同期モニカーを使用するための機能を提供します。 `CCachedDataPathProperty`オブジェクト、URL またはファイル ソースからデータを非同期的に転送しを使用して、メモリ ファイルに格納できる、`m_Cache`パブリック変数です。 メモリ ファイル内のすべてのデータが格納されているし、オーバーライドする必要はありません[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)通知を監視して応答する場合を除き、します。 たとえば、大規模なを転送する場合です。GIF ファイルをコントロールを通知より多くのデータが到着した自体が再描画するか上書き`OnDataAvailable`通知します。  
  
 クラス`CCachedDataPathProperty`から派生した`CDataPathProperty`です。  
  
 インターネット アプリケーションで非同期モニカーと ActiveX コントロールを使用する方法の詳細については、次のトピックを参照してください。  
  
- [インターネット最初のステップ: ActiveX コントロール](../../mfc/activex-controls-on-the-internet.md)  
  
- [インターネット最初のステップ: 非同期モニカー](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>継承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [関数](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 [関数](../../mfc/reference/cdatapathproperty-class.md)  
  
 `CCachedDataPathProperty`  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** afxctl.h  
  
##  <a name="ccacheddatapathproperty"></a>  CCachedDataPathProperty::CCachedDataPathProperty  
 `CCachedDataPathProperty` オブジェクトを構築します。  
  
```  
CCachedDataPathProperty(COleControl* pControl = NULL);

 
CCachedDataPathProperty(
    LPCTSTR lpszPath,  
    COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>パラメーター  
 `pControl`  
 オブジェクトへのポインター、ActiveX コントロールにこれを関連付けられる`CCachedDataPathProperty`オブジェクト。  
  
 `lpszPath`  
 可能性のある絶対または相対パス、パスは、プロパティの実際の絶対位置を参照する非同期モニカーの作成に使用します。 `CCachedDataPathProperty` ファイル名の Url を使用します。 場合は、`CCachedDataPathProperty`ファイルのオブジェクトをパスに file:// を付加します。  
  
### <a name="remarks"></a>コメント  
 `COleControl`によって指されるオブジェクト`pControl`によって使用される[開く](../../mfc/reference/cdatapathproperty-class.md#open)と派生クラスによって取得します。 場合`pControl`は**NULL**で使用されるコントロール**開く**で設定する必要があります[SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol)です。 場合`lpszPath`は**NULL**、パス経由で渡すことができます**開く**でそれを設定または[SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath)です。  
  
##  <a name="m_cache"></a>  CCachedDataPathProperty::m_Cache  
 データがキャッシュされる、メモリ ファイルのクラス名が含まれています。  
  
```  
CMemFile m_Cache;  
```  
  
### <a name="remarks"></a>コメント  
 メモリ ファイルは、ディスクではなく RAM に格納されます。  
  
## <a name="see-also"></a>関連項目  
 [関数クラス](../../mfc/reference/cdatapathproperty-class.md)   
 [階層図](../../mfc/hierarchy-chart.md)   
 [CDataPathProperty クラス](../../mfc/reference/cdatapathproperty-class.md)
