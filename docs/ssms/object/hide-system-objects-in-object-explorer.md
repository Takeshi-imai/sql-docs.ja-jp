---
title: "[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする] | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-objects
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hiding system objects
- system objects [SQL Server]
- objects [SQL Server], hiding
- Object Explorer, hiding objects
ms.assetid: c01d8804-838c-4f75-b78c-80e41e4fffdc
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2b2fc6a0c8f840bb51eb758506c08240a66820a5
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="hide-system-objects-in-object-explorer"></a>[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする]
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用して、オブジェクト エクスプローラーのシステム オブジェクトを非表示にする方法について説明します。 オブジェクト エクスプローラーの **[データベース]** ノードには、システム データベースなどのシステム オブジェクトが含まれています。 システム オブジェクトを非表示にするには、 **[ツール]**/**[オプション]** ページを使用します。 システム関数やシステム データ型など、システム オブジェクトの中にはこの設定で非表示にならないものもあります。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-hide-system-objects-in-object-explorer"></a>オブジェクト エクスプローラーでシステム オブジェクトを非表示にするには  
  
1.  **[ツール]** メニューの **[オプション]**をクリックします。  
  
2.  **[環境/スタートアップ]** ページで、 **[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする]**を選択し、 **[OK]**をクリックします。  
  
3.  この変更を有効にするには SQL Server Management Studio の再起動が必要であることを示すメッセージが表示されたら、 **[SQL Server Management Studio]** ダイアログ ボックスで **[OK]** をクリックします。  
  
4.  SQL Server Management Studio を閉じ、再度開きます。  
  
