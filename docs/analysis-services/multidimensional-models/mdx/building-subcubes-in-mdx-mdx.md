---
title: "MDX (MDX) でのサブキューブを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
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
- queries [MDX], subcubes
- subcubes [MDX]
- filtered views [MDX]
- MDX [Analysis Services], subcubes
- Multidimensional Expressions [Analysis Services], subcubes
- CREATE SUBCUBE statement
ms.assetid: 5403a62b-99ac-4d83-b02a-89bf78bf0f46
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3572204ca3619b2a7e545bdd4bca8c1717ea41c3
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="building-subcubes-in-mdx-mdx"></a>MDX でのサブキューブの作成 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
サブキューブは、基になるデータにフィルターを適用したビューを表す、キューブのサブセットです。 キューブをサブキューブに限定することによって、クエリのパフォーマンスを向上させることができます。  
  
 サブキューブを定義するには、このトピックで説明されている [CREATE SUBCUBE](../../../mdx/mdx-data-definition-create-subcube.md) ステートメントを使用します。  
  
## <a name="create-subcube-syntax"></a>CREATE SUBCUBE の構文  
 サブキューブを作成するための構文は、以下のとおりです。  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 CREATE SUBCUBE の構文は非常に単純です。 *Subcube_Identifier* パラメーターは、サブキューブの基になるキューブを識別します。 *Subcube_Expression* パラメーターでは、サブキューブにするキューブの部分を選択します。  
  
 サブキューブを作成すると、そのサブキューブは、セッションが閉じるまで、あるいは [DROP SUBCUBE](../../../mdx/mdx-data-definition-drop-subcube.md) ステートメントを実行するまですべての MDX クエリのコンテキストになります。  
  
### <a name="what-a-subcube-contains"></a>サブキューブの内容  
 CREATE SUBCUBE ステートメントの使用法は単純ですが、サブキューブに含まれるすべてのメンバーがステートメント自体で明示的に指定されるわけではありません。 サブキューブを定義する場合には、以下の規則が適用されます。  
  
-   ある階層の **(All)** メンバーを含める場合、その階層のすべてのメンバーが含まれます。  
  
-   任意のメンバーを含める場合、そのメンバーの先祖と子孫も含まれます。  
  
-   あるレベルの各メンバーを含める場合、階層のすべてのメンバーが含まれます。 他の階層のメンバーは、そのレベルのメンバーと共に存在していない場合 (たとえば、顧客を含まない都市のような不均衡階層など)、除外されます。  
  
-   サブキューブには、キューブの各 **(All)** メンバーが常に含まれます。  
  
 さらに、サブキューブ内の集計値は視覚的に合計されます。 たとえば、 `USA`、 `WA`、 `OR`を含むサブキューブがあるとします。 サブキューブによって定義されている州は `USA` と `{WA,OR}` だけなので、 `WA` の集計値は `OR` の合計になります。 他の州は無視されます。  
  
 また、サブキューブの外部にあるセルへの明示的な参照を行うと、キューブ全体のコンテキストで評価されるセル値が返されます。 たとえば、今年度に限定したサブキューブを作成するとします。 この場合、 [ParallelPeriod](../../../mdx/parallelperiod-mdx.md) 関数を使用して今年度を前年度と比較することができます。 前年度の値はサブキューブの外部にありますが、それでも値の差が返されます。  
  
 さらに、元のコンテキストを上書きしない場合、サブセレクト内で評価されるセット関数は、サブセレクトのコンテキストで評価されます。 コンテキストを上書きする場合、セット関数はキューブ全体のコンテキストで評価されます。  
  
## <a name="create-subcube-example"></a>CREATE SUBCUBE の例  
 以下の例では、Budget キューブを 4200 と 4300 のアカウントに限定するサブキューブを作成しています。  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 セッションに対するサブキューブが作成されるので、以降のクエリは、キューブ全体ではなくサブキューブに対して実行されます。 たとえば、次のクエリを実行します。 このクエリでは、アカウント 4200 と 4300 のメンバーだけが返されます。  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## <a name="see-also"></a>参照  
 [クエリ &#40; 内のキューブ コンテキストの確立MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)   
 [MDX クエリの基礎と #40 です。Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
