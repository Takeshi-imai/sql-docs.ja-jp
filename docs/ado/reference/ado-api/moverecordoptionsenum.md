---
title: MoveRecordOptionsEnum | Microsoft Docs
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
- MoveRecordOptionsEnum
helpviewer_keywords:
- MoveRecordOptionsEnum enumeration [ADO]
ms.assetid: f53c2ce4-1021-4a45-92b8-775e8bebad99
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d42dbc66f84a3b087401063ee3a53a00f2f37105
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
動作を指定します、[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクト[後続](../../../ado/reference/ado-api/moverecord-method-ado.md)メソッドです。  
  
|定数|[値]|Description|  
|--------------|-----------|-----------------|  
|**adMoveUnspecified**|-1|既定値です。 既定の移動操作を実行します。 変換先ファイルまたはディレクトリが既に存在し、操作は、ハイパー テキスト リンクを更新する場合、操作は失敗します。|  
|**adMoveOverWrite**|1|既に存在する場合でも、変換先ファイルまたはディレクトリを上書きします。|  
|**adMoveDontUpdateLinks**|2|既定の動作を変更**後続**ソースのハイパー テキスト リンクを更新しないようにすることによって**レコード**です。 既定の動作は、プロバイダーの機能に依存します。 移動操作は、プロバイダーができる場合に、リンクを更新します。 プロバイダーは、リンクを解決できない場合、またはこの値が指定されていない場合は、移動が成功したでもときのリンクが解決されていません。|  
|**adMoveAllowEmulation**|4|要求の移動 (ダウンロード、アップロード、および削除操作) をシミュレートするために、プロバイダーを試みることです。 場合に移動する、**レコード**送信先 URL とは別のサーバー上か、ソースは異なるプロバイダーによって処理される、これとが異なるプロバイダーの機能により、増加の待機時間やデータ損失が失敗した場合プロバイダー間でリソースを移動します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 これらの定数には、対応する ADO/WFC はありません。  
  
## <a name="applies-to"></a>適用対象  
 [MoveRecord メソッド (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
