---
title: "FiscalYearName 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: FiscalYearName Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: FiscalYearName
helpviewer_keywords: FiscalYearName element
ms.assetid: ce613a21-6890-4796-aac5-b029eca46255
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 422c6047fff4a3441f257a77d5a1a75a46d1dfc9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="fiscalyearname-element-assl"></a>FiscalYearName 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]会計年度の名前の命名規則を定義、 [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TimeBinding>  
   ...  
   <FiscalYearName>...</FiscalYearName>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*NextCalendarYearName*|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*CalendarYearName*|現在のカレンダー年度の名前を会計年度に割り当てます。|  
|*NextCalendarYearName*|来年のカレンダー年度の名前を会計年度に割り当てます。|  
  
 許可される値に対応する列挙**FiscalYearName**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.FiscalYearName>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
