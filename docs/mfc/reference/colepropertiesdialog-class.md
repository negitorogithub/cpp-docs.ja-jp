---
title: メンバー クラス |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
dev_langs:
- C++
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d61d773e2c35bb67f34ae2b4a989a388d8b4015
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="colepropertiesdialog-class"></a>メンバー クラス
Windows に共通の [OLE プロジェクト プロパティ] ダイアログ ボックスをカプセル化します。  
  
## <a name="syntax"></a>構文  
  
```  
class COlePropertiesDialog : public COleDialog  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="public-constructors"></a>パブリック コンストラクター  
  
|名前|説明|  
|----------|-----------------|  
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|`COlePropertiesDialog` オブジェクトを構築します。|  
  
### <a name="public-methods"></a>パブリック メソッド  
  
|名前|説明|  
|----------|-----------------|  
|[COlePropertiesDialog::DoModal](#domodal)|ダイアログ ボックスが表示され、選択を行うことができます。|  
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|ドキュメント アイテムのスケールが変更されたときに、フレームワークによって呼び出されます。|  
  
### <a name="public-data-members"></a>パブリック データ メンバー  
  
|名前|説明|  
|----------|-----------------|  
|[COlePropertiesDialog::m_gp](#m_gp)|「全般」のページを初期化するために使用する構造体、`COlePropertiesDialog`オブジェクト。|  
|[COlePropertiesDialog::m_lp](#m_lp)|「リンク」ページを初期化するために使用する構造体、`COlePropertiesDialog`オブジェクト。|  
|[COlePropertiesDialog::m_op](#m_op)|初期化するために使用する構造体、`COlePropertiesDialog`オブジェクト。|  
|[COlePropertiesDialog::m_psh](#m_psh)|追加のカスタム プロパティ ページを追加するために使用する構造。|  
|[COlePropertiesDialog::m_vp](#m_vp)|構造体の"View"ページをカスタマイズするために使用する`COlePropertiesDialog`オブジェクト。|  
  
## <a name="remarks"></a>コメント  
 共通の OLE オブジェクトのプロパティ ダイアログ ボックスでは、表示し、Windows の標準に準拠した形式での OLE ドキュメント項目のプロパティを変更する簡単な方法を提供します。 これらのプロパティには、ドキュメント、項目 (項目がリンクされている) 場合、次の項目のリンク アイコンとイメージのスケーリングと情報を表示するオプションで表されるファイル情報が、他のユーザー間で含まれます。  
  
 使用する、`COlePropertiesDialog`オブジェクト、オブジェクトを使用して、最初に作成、`COlePropertiesDialog`コンス トラクターです。 ダイアログ ボックスが構築された後、`DoModal`メンバー関数 ダイアログ ボックスが表示され、ユーザーが項目のプロパティを変更できるようにします。 `DoModal` ユーザーが、[ok] を選択するかどうかを返します ( **IDOK**) またはキャンセル ( **IDCANCEL**) ボタンをクリックします。 に加えて、[ok] と [キャンセル] ボタン、[適用] ボタンがあります。 ユーザーは、適用を選択するときにドキュメント アイテムのプロパティに加えられた変更は、項目に適用され、そのイメージに自動的に更新されますが、アクティブなままです。  
  
 [M_psh](#m_psh)データ メンバーはへのポインター、 **PROPSHEETHEADER**構造体、ほとんどの場合、明示的にアクセスする必要はありません。 既定の [全般]、ビュー、およびリンクのページを超える追加のプロパティ ページを必要がある場合は例外です。 この場合、変更することができます、`m_psh`データ メンバーを呼び出す前に、カスタム ページを含める、`DoModal`メンバー関数。  
  
 OLE ダイアログ ボックスの詳細については、記事を参照してください。 [OLE のダイアログ ボックス](../../mfc/dialog-boxes-in-ole.md)です。  
  
## <a name="inheritance-hierarchy"></a>継承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePropertiesDialog`  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** afxodlgs.h  
  
##  <a name="colepropertiesdialog"></a>  COlePropertiesDialog::COlePropertiesDialog  
 
          `COlePropertiesDialog` オブジェクトを作成します。  
  
```  
COlePropertiesDialog(
    COleClientItem* pItem,  
    UINT nScaleMin = 10,  
    UINT nScaleMax = 500,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>パラメーター  
 `pItem`  
 アクセスされるプロパティを持つドキュメント項目へのポインター。  
  
 *nScaleMin*  
 最小のドキュメント アイテムのイメージの倍率します。  
  
 *nScaleMax*  
 ドキュメント アイテムのイメージの倍率を最大数です。  
  
 `pParentWnd`  
 ダイアログ ボックスの親または所有者へのポインター。  
  
### <a name="remarks"></a>コメント  
 共通の OLE オブジェクトのプロパティ ダイアログのクラスを派生`COlePropertiesDialog`ドキュメント項目のスケーリングを実装するためにします。 このクラスのインスタンスによって実装されたすべてのダイアログ ボックスは、ドキュメント アイテムのスケーリングをサポートしていません。  
  
 既定では、共通の OLE オブジェクトのプロパティ ダイアログ ボックスでは、次の 3 つの既定のページがあります。  
  
-   全般  
  
     このページには、選択されているドキュメント項目によって表されるファイルのシステム情報が含まれています。 このページから、ユーザーは、別の型を選択した項目を変換できます。  
  
-   表示  
  
     このページには、アイテムを表示する、アイコンの変更、およびイメージのスケーリングを変更するためのオプションが含まれています。  
  
-   リンク  
  
     このページには、リンク アイテムの場所を変更して、リンク アイテムの更新のオプションが含まれています。 このページから、ユーザーが選択された項目のリンクを分割できます。  
  
 既定で提供されるもの以外のページを追加、変更、 [m_psh](#m_psh)メンバー変数のコンス トラクターを終了する前に、 `COlePropertiesDialog`-クラスを派生します。 これは、高度な実装、`COlePropertiesDialog`コンス トラクターです。  
  
##  <a name="domodal"></a>  COlePropertiesDialog::DoModal  
 Windows コモン OLE オブジェクトのプロパティ ダイアログ ボックスを表示し、ユーザーが閲覧またはドキュメント アイテムのさまざまなプロパティを変更できるようにするには、このメンバー関数を呼び出します。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>戻り値  
 **IDOK**または**IDCANCEL**成功、0 以外の場合。 **IDOK**と**IDCANCEL**ユーザーが、[ok] または [キャンセル] ボタンを選択するかどうかを示す定数です。  
  
 場合**IDCANCEL** 、Windows を呼び出すことができます、返される[情報を得る](http://msdn.microsoft.com/library/windows/desktop/ms646916)エラーが発生したかどうかを判断する関数。  
  
##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp  
 型の構造体[OLEUIGNRLPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687297)OLE オブジェクトのプロパティ ダイアログ ボックスの [全般] ページを初期化するために使用される、します。  
  
```  
OLEUIGNRLPROPS m_gp;  
```  
  
### <a name="remarks"></a>コメント  
 このページは、埋め込まれたアイテムのサイズと種類を表示し、[変換] ダイアログ ボックスへのアクセスを許可します。 このページには、かどうか、オブジェクトは、リンクのリンク先も表示されます。  
  
 詳細については、 **OLEUIGNRLPROPS**構造体、Windows SDK を参照してください。  
  
##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp  
 型の構造体[OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735)OLE オブジェクトのプロパティ ダイアログ ボックスの [リンク] ページを初期化するために使用される、します。  
  
```  
OLEUILINKPROPS m_lp;  
```  
  
### <a name="remarks"></a>コメント  
 このページは、リンク アイテムの場所を表示し、更新、またはアイテムへのリンクを解除することができます。  
  
 詳細については、 **OLEUILINKPROPS**構造体、Windows SDK を参照してください。  
  
##  <a name="m_op"></a>  COlePropertiesDialog::m_op  
 型の構造体[OLEUIOBJECTPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687199)、共通の OLE オブジェクトのプロパティ ダイアログ ボックスを初期化するために使用します。  
  
```  
OLEUIOBJECTPROPS m_op;  
```  
  
### <a name="remarks"></a>コメント  
 この構造体には、[全般]、リンク、およびビュー ページを初期化するために使用されるメンバーが含まれています。  
  
 詳細については、次を参照してください。、 **OLEUIOBJECTPROPS**と[OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735) Windows SDK 内の構造体。  
  
##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh  
 型の構造体[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)メンバーのダイアログ オブジェクトの特性を格納します。  
  
```  
PROPSHEETHEADER m_psh;  
```  
  
### <a name="remarks"></a>コメント  
 構築した後、`COlePropertiesDialog`オブジェクトを使用する`m_psh`を呼び出す前に ダイアログ ボックスのさまざまな側面を設定する、`DoModal`メンバー関数。  
  
 変更する場合、`m_psh`データ メンバーを直接、既定の動作がオーバーライドされます。  
  
 詳細については、 **PROPSHEETHEADER**構造体、Windows SDK を参照してください。  
  
##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp  
 型の構造体[OLEUIVIEWPROPS](http://msdn.microsoft.com/library/windows/desktop/ms693751)OLE オブジェクトのプロパティ ダイアログ ボックスの [表示] ページを初期化するために使用される、します。  
  
```  
OLEUIVIEWPROPS m_vp;  
```  
  
### <a name="remarks"></a>コメント  
 このページでは、ユーザーを"content"と「アイコン化」のビュー、オブジェクトの間で切り替えるし、コンテナー内でスケールを変更します。 アイコンの変更 ダイアログ ボックスへのユーザー アクセスは、オブジェクトがアイコンとして表示されているときにこともできます。  
  
 詳細については、 **OLEUIVIEWPROPS**構造体、Windows SDK を参照してください。  
  
##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale  
 スケーリングの値が変更されており、ok または 適用が選択されたときに、フレームワークによって呼び出されます。  
  
```  
virtual BOOL OnApplyScale(
    COleClientItem* pItem,  
    int nCurrentScale,  
    BOOL bRelativeToOrig);
```  
  
### <a name="parameters"></a>パラメーター  
 `pItem`  
 アクセスされるプロパティを持つドキュメント項目へのポインター。  
  
 `nCurrentScale`  
 ダイアログのスケールの数値を設定します。  
  
 *bRelativeToOrig*  
 ドキュメント項目の元のサイズにスケーリングを適用するかどうかを示します。  
  
### <a name="return-value"></a>戻り値  
 0 以外の場合は、次の処理です。それ以外の場合 0 を返します。  
  
### <a name="remarks"></a>コメント  
 既定の実装では、何も行われません。 スケーリングの制御を有効にするには、この関数をオーバーライドする必要があります。  
  
> [!NOTE]
>  共通の OLE オブジェクトのプロパティ ダイアログ ボックスが表示される前に、フレームワークでは、この関数は**NULL**の`pItem`- 1 を`nCurrentScale`です。 これは、スケーリングの制御を有効にするかどうかを決定します。  
  
## <a name="see-also"></a>関連項目  
 [MFC サンプル CIRC](../../visual-cpp-samples.md)   
 [関数クラス](../../mfc/reference/coledialog-class.md)   
 [階層図](../../mfc/hierarchy-chart.md)   
 [関数クラス](../../mfc/reference/coledialog-class.md)   
 [CPropertyPage クラス](../../mfc/reference/cpropertypage-class.md)
