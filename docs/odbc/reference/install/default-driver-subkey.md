---
title: "既定のドライバーのサブキー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb867819985d1466b00cb048f91d8aa99c35cdd0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="default-driver-subkey"></a>既定のドライバーのサブキー
既定のサブキーには、既定のデータ ソースで使用するドライバーを説明する 1 つの値が含まれています。 この値の形式は次の表に示します。  
  
|[オブジェクト名]|データ型|data|  
|----------|---------------|----------|  
|**[ドライバー]**|REG_SZ|*既定のドライバーの説明*|  
  
 *既定ドライバー説明*名前は、ドライバーを説明する ODBC ドライバーのサブキーの下の値の名前と同じです。  
  
 たとえば、既定のデータ ソースは、SQL Server のドライバーを使用している場合、既定のサブキーの下の値が開く場合があります。  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  既定のサブキーに含まれている既定のドライバーは、既定のユーザー DSN または既定のシステム DSN のいずれかを参照できます。 最初に作成された DSN として有効なエントリができない可能性がありますので DSN が作成された既定のユーザー DSN と既定のシステムの両方場合は、既定のドライバーが 最後に、作成された DSN によって決まります。
