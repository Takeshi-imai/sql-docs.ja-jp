---
title: "スキーマ要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Schema Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Schema
helpviewer_keywords:
- Schema element
ms.assetid: 4b6375fb-7ad8-4d5f-88b1-abd3da2654db
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 51fd142bad60a7c8e64d27952509dfa5b2b6c28f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="schema-element-assl"></a>Schema 要素 (ASSL)
  データ ソース ビューのスキーマを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSourceView>  
   ...  
   <Schema>...</Schema>  
   ...  
</DataSourceView>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|スキーマ|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **スキーマ**のデータセットの XML スキーマ定義 (XSD) 言語形式を使用して表される、[!INCLUDE[msCoName](../../../includes/msconame-md.md)]データセットおよびその他のデータの定義におけるこの使用方法に固有の拡張することで、.NET Framework言語 (DDL)。 データセットは、XSD からリレーショナル スキーマへの柔軟なマッピングを定義しますが、より正規の形式で XSD を返します。 データ ソースでは、この正規の形式だけが有効です。  
  
 親に対応する要素**スキーマ**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DataSourceView>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  