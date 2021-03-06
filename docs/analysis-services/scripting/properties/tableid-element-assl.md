---
title: "TableID 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: TableID Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TableID
helpviewer_keywords: TableID element
ms.assetid: 45fe7e23-b274-4bc2-be63-1a5bb6680f51
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e3b3e6f80c157dbb867aaf4362a39e6ed91cd974
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="tableid-element-assl"></a>TableID 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]テーブルの識別子 (ID) が含まれています (から、 [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)要素)、親要素に関連付けられています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ColumnBinding> <!-- or DSVTableBinding, RowBinding, IncrementalProcessingNotification -->  
   ...  
   <TableID>...</TableID>  
   ...  
</ColumnBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|基数|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)、 [DSVTableBinding](../../../analysis-services/scripting/data-type/dsvtablebinding-data-type-assl.md)、 [IncrementalProcessingNotification](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md)、 [RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 によって識別されるテーブル**TableID**所有オブジェクト (ディメンションまたはキューブ) がバインドされているデータ ソース内である必要があります。  
  
 親に対応する要素**TableID**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.ColumnBinding>、 <xref:Microsoft.AnalysisServices.DSVTableBinding>、 <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>、および<xref:Microsoft.AnalysisServices.RowBinding>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
