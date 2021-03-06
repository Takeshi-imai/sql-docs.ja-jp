---
title: DISCOVER_PARTITION_STAT Rowset | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 20d339e2-f47f-437f-94d5-5b00b400356a
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 649475fa5fd1a4e0bb2a6c734f916270ac7f9a64
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="discoverpartitionstat-rowset"></a>DISCOVER_PARTITION_STAT 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
特定のパーティションの集計に関する統計を返します。  
  
 **適用されます:**表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_PARTITION_STAT**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|必須|ディメンションを含むデータベースの名前。<br /><br /> この列は制限リストに必要です。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|必須|パーティションを含むキューブまたはテーブル モデルの名前です。<br /><br /> この列は制限リストに必要です。|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|必須|ディメンション内のメジャー グループの名前です。<br /><br /> この列は制限リストに必要です。|  
|**PARTITION_NAME**|**DBTYPE_WSTR**|必須|パーティションの名前。<br /><br /> この列は制限リストに必要です。|  
|**AGGREGATION_NAME**|**DBTYPE_WSTR**||集計の名前です。|  
|**AGGREGATION_SIZE**|**DBTYPE_I8**||集計のサイズです。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd8f-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionStat|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
