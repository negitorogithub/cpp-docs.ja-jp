---
title: コンパイラ エラー C2731 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2731
dev_langs:
- C++
helpviewer_keywords:
- C2731
ms.assetid: 9b563999-febd-4582-9147-f355083c091e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f925a781501b2dfd3ed2297319d49cc27854a78a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2731"></a>コンパイラ エラー C2731
'identifier': 関数はオーバー ロードできません  
  
 関数は、 `main`、 `WinMain`、 `DllMain`、および`LibMain`オーバー ロードすることはできません。  
  
 次の例では、C2731 が生成されます。  
  
```  
// C2731.cpp  
extern "C" void WinMain(int, char *, char *);  
void WinMain(int, short, char *, char*);   // C2731  
```