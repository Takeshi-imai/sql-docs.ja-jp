---
title: "Visual C アプリケーションで ADO ライブラリを参照する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: "“drivers”"
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a554ff290c1ea3fa8ef5382e45fafbae5b1110d8
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Visual C アプリケーションで ADO ライブラリを参照します。
Visual C アプリケーションで ADO の最新バージョンを使用するには、次を使用`#import`ディレクティブ。  
  
```  
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 インポートする必要がありますまたはを使用する ADO MD ADOX、 *msadomd.dll*または*msadox.dll*、上記の構文を使用しています。  
  
## <a name="backward-compatibility"></a>旧バージョンとの互換性  
 ADO の以前のバージョンを使用するのには、置換*msado15.dll*上で次のタイプ ライブラリのいずれか。  
  
-   *msado27.tlb*、ADO 2.7 タイプ ライブラリ  
  
-   *msado26.tlb*、ADO 2.6 のタイプ ライブラリ  
  
-   *msado25.tlb*、ADO 2.5 のタイプ ライブラリ  
  
-   *msado21.tlb*、ADO 2.1 のタイプ ライブラリ  
  
-   *msado20.tlb*, ADO 2.0 Type Library
