---
title: LockTypeEnum | Microsoft Docs
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
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f9fe62c251092eb182925de0fa7b6d70c359a25d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="locktypeenum"></a>LockTypeEnum
編集中のレコードに適用されるロックの種類を指定します。  
  
|定数|[値]|Description|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|オプティミスティック バッチ更新を示します。 バッチ更新モードに必要です。|  
|**adLockOptimistic**|3|オプティミスティック ロック、レコード単位を示します。 ロックの使用、オプティミスティック ロックのレコードを呼び出すときにのみ、[更新](../../../ado/reference/ado-api/update-method.md)メソッドです。|  
|**adLockPessimistic**|2|レコードごとの排他的ロックを指定します。 プロバイダーはどのような成功レコードの編集、通常で編集した後すぐに、データ ソースのレコードのロックを保つために必要です。|  
|**adLockReadOnly**|1|読み取り専用のレコードを示します。 データを変更することはできません。|  
|**adLockUnspecified**|-1|ロックの種類は指定しません。 クローンが、元と同じロックの種類と、複製が作成されます。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.LockType.BATCHOPTIMISTIC|  
|AdoEnums.LockType.OPTIMISTIC|  
|AdoEnums.LockType.PESSIMISTIC|  
|AdoEnums.LockType.READONLY|  
|AdoEnums.LockType.UNSPECIFIED|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Clone メソッド (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[LockType プロパティ (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Open メソッド (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[WillExecute イベント (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
