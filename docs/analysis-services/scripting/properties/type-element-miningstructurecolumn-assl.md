---
title: "Type 要素 (MiningStructureColumn) (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Type Element (MiningStructureColumn)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TYPE
helpviewer_keywords: Type element
ms.assetid: ce999716-9487-4348-bc42-270a2026a452
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: edbbd08e5086157866ff5738d171614925c681cb
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="type-element-miningstructurecolumn-assl"></a>Type 要素 (MiningStructureColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]型を含む、 [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructureColumn>  
   ...  
   <Type>...</Type>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|基数|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|*長い*|64 ビットの符号付き整数です。 このデータ型にマップ、 **Int64**のデータ型の[!INCLUDE[msCoName](../../../includes/msconame-md.md)]OLE DB に .NET Framework と DBTYPE_I8 データを入力します。|  
|*ブール値*|ブール値です。 このデータ型にマップ、**ブール**.NET Framework と OLE DB の DBTYPE_BOOL データ型でのデータ型。|  
|*テキスト*|Unicode 文字の NULL 終了ストリームです。 このデータ型にマップ、**文字列**.NET Framework と OLE DB の DBTYPE_WSTR データ型でのデータ型。|  
|*Double*|範囲内で倍精度浮動小数点数-1.79 e +308 ~ 1.79 です。 このデータ型にマップ、**二重**.NET Framework と OLE DB の DBTYPE_R8 データ型でのデータ型。|  
|*日付*|倍精度浮動小数点数として保存される日付データ。 整数部分は 1899 年 12 月 30 日からの日数で、小数部分は日の端数です。 このデータ型にマップ、 **DateTime** .NET Framework と OLE DB の DBTYPE_DATE データ型でのデータ型。|  
|*Table*|入れ子になったテーブル。 このデータ型は、OLE DB の DBTYPE_HCHAPTER データ型にマップされます。<br /><br /> 注: .NET Framework でのテーブル列は、同等の組み込みデータ型はありませんでサポートされる代わりに、 **DataReader**クラスです。|  
  
 許可される値に対応する列挙**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>します。  
  
 親に対応する要素**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructureColumn>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
