---
title: "コマンド要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Command Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Command
helpviewer_keywords: Command element
ms.assetid: 277598b5-9939-4d7f-8c75-06470c3fabdd
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8a4c40a6e277759596db53844b00edc78a06ba21
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="command-element-assl"></a>Command 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]親要素のコンテキスト内で使用可能であるコマンドを定義、[コマンド](../../../analysis-services/scripting/collections/commands-element-assl.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Commands>  
   <Command>  
      <Text>...</Text>  
   </Command>  
</Commands >  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[コマンド]](../../../analysis-services/scripting/collections/commands-element-assl.md)|  
|子要素|[テキスト](../../../analysis-services/scripting/properties/text-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Command>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
