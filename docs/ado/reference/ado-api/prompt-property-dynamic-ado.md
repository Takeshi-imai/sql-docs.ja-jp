---
title: "動的プロパティ (ADO) を求める |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 02f6a8423aac843adf90b4ea865b910d55f89bd6
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="prompt-property-dynamic-ado"></a>プロンプトのプロパティ-動的 (ADO)
OLE DB プロバイダーが初期化情報のユーザーの入力を求める必要があるかどうかを指定します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定を返します、 [ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)値。  
  
## <a name="remarks"></a>解説  
 **プロンプト**、動的なプロパティを追加することは、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)OLE DB プロバイダーによるコレクション。 初期化情報を要求するには、OLE DB プロバイダーは、ダイアログ ボックスをユーザーに通常表示されます。  
  
 動的なプロパティ、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトが失われたときに、**接続**が閉じられます。 **プロンプト**再を開く前にプロパティをリセットする必要があります、**接続**既定以外の値を使用します。  
  
> [!NOTE]
>  プロバイダーが、ユーザーことはできません ダイアログ ボックスに応答するシナリオでユーザーを求める必要がありますを指定しません。 たとえば、ユーザーはアプリケーションがユーザーのクライアントではなく、サーバー システムで実行されている場合、またはユーザーがログオンしていないアプリケーションがシステムで実行されている場合に応答することができません。 このような場合、アプリケーションは応答を無期限に待機しがロックされていないと思われます。  
  
## <a name="usage"></a>使用方法  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
