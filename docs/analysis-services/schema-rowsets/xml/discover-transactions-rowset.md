---
title: "DISCOVER_TRANSACTIONS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 85789177-c5df-4336-a90c-c20d69277ab4
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0b287af43de1284c727a64d27d55b3ccf75c5d87
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="discovertransactions-rowset"></a>DISCOVER_TRANSACTIONS 行セット
  現在システムで保留中のトランザクションのセットを返します。  
  
 **適用されます:**表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_TRANSACTIONS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**TRANSACTION_ID**|**DBTYPE_WSTR**|トランザクション、一意な識別子として GUID。|  
|**TRANSACTION_SESSION_ID**|**DBTYPE_WSTR**|GUID としてのトランザクション セッションの一意識別子。|  
|**TRANSACTION_START_TIME**|**DBTYPE_DBTIMESTAMP**|トランザクションが開始されたときのサーバーの UTC 日時。|  
|**TRANSACTION_ELAPSED_TIME_MS**|**DBTYPE_I8**|トランザクションが開始されてからの経過時間 (ミリ秒単位)。|  
|**TRANSACTION_CPU_TIME_MS**|**DBTYPE_I8**|トランザクションの開始以降にすべての要求で使用された CPU 時間 (ミリ秒単位)。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_TRANSACTIONS**行セットは、次の表に示されている列で制限できます。  
  
|**列名**|**型インジケーター**|**制限の状態**|  
|---------------------|------------------------|---------------------------|  
|**ID**|**DBTYPE_WSTR**|省略可。|  
|**SESSION_ID**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd28-8148-11d0-87bb-00c04fc33942|  
|文字列|DISCOVER_TRANSACTIONS|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  