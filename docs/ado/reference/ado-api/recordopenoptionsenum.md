---
title: RecordOpenOptionsEnum | Microsoft Docs
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
f1_keywords:
- RecordOpenOptionsEnum
helpviewer_keywords:
- RecordOpenOptionsEnum enumeration [ADO]
ms.assetid: 9028aba4-90fc-4dfc-88e4-fa8a7b6fedee
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 56caae53741a24727763868295ca92216557323c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="recordopenoptionsenum"></a>RecordOpenOptionsEnum
開くのためのオプションを指定します、[レコード](../../../ado/reference/ado-api/record-object-ado.md)です。 使用してこれらの値を組み合わせることができますか。  
  
|定数|[値]|Description|  
|--------------|-----------|-----------------|  
|**adDelayFetchFields**|0x8000|フィールドが関連付けられているプロバイダーを示す、**レコード**最初に、取得する必要がありませんが、フィールドにアクセスする最初の試行に取得できます。 ない場合、このフラグで示される、既定の動作がすべて取得するには、**レコード**オブジェクトのフィールドです。|  
|**adDelayFetchStream**|0x4000|既定のストリームが関連付けられているプロバイダーを示す、**レコード**最初に取得する必要がありません。 関連付けられている既定のストリームを取得することがない場合、このフラグで示される、既定の動作です、**レコード**オブジェクト。|  
|**adOpenAsync**|0x1000|示します、**レコード**オブジェクトは非同期モードで開きます。|  
|**adOpenExecuteCommand**|0x10000|ソース文字列が実行されるコマンド テキストが含まれていることを示します。 この値は、 **adCmdText**オプションを**Recordset.Open**です。|  
|**adOpenRecordUnspecified**|-1|既定値です。 オプションが指定されていないことを示します。|  
|**adOpenOutput**|0x800000|ソースが実行可能ファイルのスクリプトを含むノードを指している場合は、ことを示します (など、します。ASP ページの場合)、し、開かれている**レコード**実行されたスクリプトの結果にが含まれます。 この値は、コレクション以外のレコードを含む有効なのみです。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 これらの定数には、対応する ADO/WFC はありません。  
  
## <a name="applies-to"></a>適用対象  
 [Open メソッド (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)
