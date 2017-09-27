---
title: "ドリルスルーを使用して、ソース データ (MDX) を取得する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9470c5edd50bab3622ad73f3e3404a4747b07dd7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-data-manipulation---retrieve-source-data-using-drillthrough"></a>MDX データ操作のドリルスルーを使用してソース データを取得します。
  多次元式 (MDX) では、キューブ セルのソース データから行セットを取得するために [DRILLTHROUGH](../../../mdx/mdx-data-manipulation-drillthrough.md)ステートメントを使用します。  
  
 キューブに対して **DRILLTHROUGH** ステートメントを実行するには、そのキューブに対するドリルスルー アクションを定義する必要があります。 ドリルスルー アクションを定義するには、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]のキューブ デザイナーの **[アクション]** ペインで、ツール バーの **[新しいドリルスルー アクション]**をクリックします。 新しいドリルスルー アクションでは、アクションの名前、対象、条件を指定し、 **DRILLTHROUGH** ステートメントによって返される列を指定します。  
  
## <a name="drillthrough-statement-syntax"></a>DRILLTHROUGH ステートメントの構文  
 **DRILLTHROUGH** ステートメントの構文は、以下のとおりです。  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 **SELECT** 句は、取得対象のソース データが入っているキューブ セルを識別します。 この **SELECT** 句は MDX の通常の **SELECT** ステートメントとほぼ同じですが、 **SELECT** 句の場合、それぞれの軸上で 1 つのメンバーだけを指定できます。 1 つの軸で複数のメンバーが指定されている場合、エラーが発生します。  
  
 構文 `<Max_Rows>` は、返されるそれぞれの行セットにおける行の最大数を指定します。 データ ソースとの接続に使われる OLE DB プロバイダーが **DBPROP_MAXROWS**をサポートしない場合、 `<Max_Rows>` の設定は無視されます。  
  
 構文 `<First_Rowset>` は、どのパーティションの行セットが最初に返されるかを識別します。  
  
 構文 `<Return_Columns>` は、基になるデータベースのどの列が返されるかを識別します。  
  
## <a name="drillthrough-statement-example"></a>DRILLTHROUGH ステートメントの例  
 以下の例は、 **DRILLTHROUGH** ステートメントの使用方法を示しています。 この例の DRILLTHROUGH ステートメントは、Stores ディメンション (スライサー軸) 上の Store、Product、Time ディメンションのリーフを照会して、部門メジャー グループ、部門 ID、従業員の名前を返します。  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a>参照  
 [データの操作 (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-manipulating-data.md)  
  
  