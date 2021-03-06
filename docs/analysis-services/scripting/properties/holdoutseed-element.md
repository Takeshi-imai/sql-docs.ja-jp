---
title: "HoldoutSeed 要素 |Microsoft ドキュメント"
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
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: HoldoutSeed
helpviewer_keywords: HoldoutSeed element
ms.assetid: 6b608bb3-c075-4744-9722-f5fb9fa1cc7e
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 910372435e504efb7afabfe245bba65e430fe1d4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="holdoutseed-element"></a>HoldoutSeed 要素
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]テスト セットを含む反復可能な提示されたパーティションのシードを指定します、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)要素。 このシードを指定すると、再処理中にモデルのコンテンツが変更されることはありません。 指定されていないか 0 に設定する場合[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]マイニング構造の名前のハッシュ アルゴリズムを使用して、シードを作成します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutSeed>...</ddl100_100:HoldoutSeed>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|Long|  
|既定値|0|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 最初にマイニング構造を作成した時点では、ID と名前は同じです。 ただし、マイニング構造の名前は変更できます。 したがって、パーティションを反復可能にする場合は、名前に基づいて作成されたシードは使用せずに、シードを明示的に設定してください。  
  
 さらを使用してマイニング構造のコピーを作成する場合、**エクスポート**ステートメントでは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]新しいマイニング構造の名前が保持されますが、新しい ID を自動的に生成されます したがって、名前が同じで ID が異なる 2 つのマイニング構造が存在することもありえます。 名前が同じ 2 つのマイニング構造では、同じシードが使用されます。 ただし、データのパーティション分割はソース データにも依存するので、各構造のパーティションの実際の内容は異なる場合があります。  
  
 新しいプロパティ**HoldoutMaxCases**、 **HoldoutMaxPercent**、 **HoldoutSeed**、または**HoldoutActualSize** でしか使用できません。[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]以降のバージョン。 構文の説明に示すように、これらのプロパティを新しい名前空間を付ける必要がありますので、または[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]はエラーを返します。  
  
 **注**で[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]でした、マイニング構造に提示されたパーティションの使用をサポートしていません。 したがって、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]スクリプト言語 (ASSL) ステートメントを提示されたパラメーターを含む**HoldoutMaxCases**、 **HoldoutMaxPercent**、 **HoldoutSeed**、または**HoldoutActualSize**では使用できません[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]です。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の ASSL ステートメントでこれらの提示されたパラメーターのいずれかを使用すると、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でエラーが返されます。  
  
 親に対応する要素**HoldoutSeed**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructure>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [HoldoutActualSize 要素](../../../analysis-services/scripting/properties/holdoutactualsize-element.md)   
 [HoldoutMaxPercent 要素](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [HoldoutMaxCases 要素](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)  
  
  
