---
title: "データ型 (データ マイニング) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [data mining]
- columns [data mining], data types
- data mining [Analysis Services], data types
ms.assetid: 4af5b7db-790b-459c-b2b4-00f0cf6b5ce4
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7e5d09435546cf0605bb7b70a685021612fd2f9b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="data-types-data-mining"></a>データ型 (データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でマイニング モデルまたはマイニング構造を作成する場合は、マイニング構造のそれぞれの列に対してデータ型を定義する必要があります。 分析エンジンは、データ型に基づいて、データ ソース内のデータが数値とテキストのどちらであるか、およびデータをどのように処理するかを判断します。 たとえば、ソース データに数値データが含まれる場合、数値を整数として扱うかまたは小数点を使用して扱うかを指定できます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、では、マイニング構造列に対して次のデータ型がサポートされています。  
  
|データ型|サポートされているコンテンツの種類|  
|---------------|-----------------------------|  
|**テキスト**|Cyclical、Discrete、Discretized、Key Sequence、Ordered、Sequence|  
|**Long**|Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time、Ordered、Sequence、Time<br /><br /> 分類済み|  
|**ブール値**|Cyclical、Discrete、Ordered|  
|**Double**|Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time、Ordered、Sequence、Time<br /><br /> 分類済み|  
|**日付**|Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time、Ordered|  
  
> [!NOTE]  
>  コンテンツの種類のうち Time および Sequence は、サード パーティのアルゴリズムでのみサポートされています。 コンテンツの種類 Cyclical および Ordered はサポートされますが、多くのアルゴリズムはこれらを不連続の値として扱い、特別な処理は行いません。  
  
 この表には、データ型ごとにサポートされている *コンテンツの種類* もまとめられています。  
  
 このコンテンツの種類はデータ マイニングに固有であり、マイニング モデルで列のデータをどのように処理または計算するかをカスタマイズできます。 たとえば、列に数字が含まれているときでも、場合によっては、離散値としてモデル化する必要があります。 列に数字が含まれている場合、ビン化または離散化するように指定したり、モデルで連続値として処理するように指定したりすることもできます。 そのため、コンテンツの種類はモデルに大きな影響を与えます。 すべてのコンテンツの種類の一覧については、「 [コンテンツの種類 (データ マイニング)](../../analysis-services/data-mining/content-types-data-mining.md)」を参照してください。  
  
> [!NOTE]  
>  他の機械学習システムでは、 *名義データ*、 *要因* 、 *カテゴリ*、 *順序データ*、 *配列データ*といった用語が使われることがあります。 一般的に、これらの用語はコンテンツの種類に相当します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、データ型により、モデルにおけるその使用ではなく、ストレージのための値型だけが指定されます。  
  
## <a name="specifying-a-data-type"></a>データ型の指定  
 データ マイニング拡張機能 (DMX) を使用してマイニング モデルを直接作成する場合は、モデルを定義するときにそれぞれの列のデータ型を定義できます。Analysis Services は、指定されたデータ型を持つ対応するマイニング構造を同時に作成します。 ウィザードを使用してマイニング モデルまたはマイニング構造を作成する場合は、Analysis Services によってデータ型が提案されます。一覧からデータ型を選択することもできます。  
  
## <a name="changing-a-data-type"></a>データ型の変更  
 列のデータ型を変更する場合は、マイニング構造およびその構造に基づくすべてのマイニング モデルを必ず再処理する必要があります。 データ型を変更する場合、特定のモデルでその列を使用できない場合があります。 その場合、Analysis Services は、モデルの再処理時にエラーを発生するか、またはその特定の列を除外してモデルを処理します。  
  
## <a name="see-also"></a>参照  
 [コンテンツの種類 (&) #40 です。 データ マイニング &#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [コンテンツの種類 &#40;DMX&#41;](../../dmx/content-types-dmx.md)   
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [マイニング構造と #40 です。Analysis Services - データ マイニング &#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [データ型 &#40;DMX&#41;](../../dmx/data-types-dmx.md)   
 [マイニング モデル列](../../analysis-services/data-mining/mining-model-columns.md)   
 [マイニング構造列](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
