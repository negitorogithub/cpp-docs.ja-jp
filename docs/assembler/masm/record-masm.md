---
title: レコード (MASM) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- RECORD
dev_langs:
- C++
helpviewer_keywords:
- RECORD directive
ms.assetid: c83db394-0fe3-468f-813f-13302cdc862d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e726053a9146cf88ed4e84045118d19b7094ed37
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="record-masm"></a>RECORD (MASM)
指定したフィールドから成るレコードの種類を宣言します。 *fieldname* 、フィールドの名前*幅*ビット単位の数を指定し、*式*その初期値を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
  
   recordname RECORD fieldname:width [[= expression]]   
[[, fieldname:width [[= expression]]]]...  
```  
  
## <a name="see-also"></a>関連項目  
 [ディレクティブ リファレンス](../../assembler/masm/directives-reference.md)