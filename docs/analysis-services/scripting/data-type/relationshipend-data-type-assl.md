---
title: "RelationshipEnd データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
ms.assetid: 3a974dd4-e1d6-45b2-b8c8-1a914bc13a02
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 58e279c57e7364c108a930038c66846844f31d5e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="relationshipend-data-type-assl"></a>RelationshipEnd データ型 (ASSL)
  リレーションシップのリレーションシップ End を表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<RelationshipEnd>  
   <Role>...</Role>  
   <Multiplicity>...</Multiplicity>  
   <DimensionID>...</DimensionID>  
   <Attributes>...</Attributes>  
   <Translations>...</Translations>  
   <VisualizationProperties>...</VisualizationProperties>  
</Relationship>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[リレーションシップ](../../../analysis-services/scripting/data-type/relationship-data-type-assl.md)|  
|子要素|[ロール](../../../analysis-services/xmla/xml-elements-properties/role-element-xmla.md)、[多重度](../../../analysis-services/scripting/properties/multiplicity-element-assl.md)、 [DimensionID](../../../analysis-services/scripting/properties/dimensionid-element-assl.md)、[属性](../../../analysis-services/scripting/collections/attributes-element-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)、 [VisualizationProperties](../../../analysis-services/scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|派生要素||  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.RelationshipEnd>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  