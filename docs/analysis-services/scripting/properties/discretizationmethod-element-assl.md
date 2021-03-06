---
title: "DiscretizationMethod 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: DiscretizationMethod Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DiscretizationMethod
helpviewer_keywords: DiscretizationMethod element
ms.assetid: 4cfe015f-ad6c-47e1-8aff-c9c7677867b1
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fd84d0426afa9ee1272c26c8ca7ac302972748b4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="discretizationmethod-element-assl"></a>DiscretizationMethod 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]分離に使用するメソッドを定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationMethod>...</DiscretizationMethod>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*なし*|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)、 [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、 **DiscretizationMethod**要素を決定する方法の値を**DimensionAttribute**または**ScalarMiningStructureColumn**分離されるか、構成されています特定のグループ セットにします。 分離メソッドの詳細については、次を参照してください。[分離メソッド (&) #40 です。 データ マイニング &#41;](../../../analysis-services/data-mining/discretization-methods-data-mining.md)です。  
  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*自動*|マイニング構造列における AUTOMATIC 分離メソッドに相当します。|  
|*EqualAreas*|マイニング構造列における EQUAL_AREAS 分離メソッドに相当します。|  
|*クラスター*|マイニング構造列における CLUSTERS 分離メソッドに相当します。|  
|*しきい値*|マイニング構造列における THRESHOLDS 分離メソッドに相当します。|  
|*EqualRanges*|マイニング構造列における EQUAL_RANGES 分離メソッドに相当します。|  
  
 許可される値に対応する列挙**DiscretizationMethod**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DiscretizationMethod>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
