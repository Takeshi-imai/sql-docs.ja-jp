---
title: "基本的な MDX スクリプト (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- default MDX scripts
- statements [MDX]
- expressions [MDX], scripts
- scripts [MDX], about scripts
ms.assetid: 83d9afda-7d34-42b5-8f28-20172a905f23
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 22da0a7df618db320214f19a73e2047ea4b37922
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="the-basic-mdx-script-mdx"></a>基本的な MDX スクリプト (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
多次元式 (MDX) スクリプトは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] におけるキューブの計算処理を定義します。 MDX スクリプトには、以下の 2 種類があります。  
  
 **既定の MDX スクリプト**  
 キューブを作成すると、そのキューブの既定の MDX スクリプトが [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって作成されます。 このスクリプトは、キューブ全体の計算パスを定義します。  
  
 **ユーザー定義の MDX スクリプト**  
 キューブを作成した後で、キューブの計算機能を拡張するためにユーザー定義の MDX スクリプトを追加することができます。  
  
## <a name="the-default-mdx-script"></a>既定の MDX スクリプト  
 キューブを定義したときに [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって作成される既定の MDX スクリプトには、CALCULATE ステートメントが 1 つ入っています。 この単一の CALCULATE ステートメントは既定の MDX スクリプトの先頭に置かれており、最初の計算パスでキューブ全体が計算されるということを示しています。  
  
 既定の MDX スクリプトには、キューブ デザイナーで作成された、名前付きセット、割り当て、および計算されるメンバーを作成するためのスクリプト コマンドも入ります。  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は既定の MDX スクリプトに直接スクリプト コマンドを追加します。  
  
-   キューブ内の名前付きセットごとに、対応する CREATE SET ステートメントが既定の MDX スクリプトに存在します。  
  
-   キューブに定義されている計算されるメンバーごとに、対応する CREATE MEMBER ステートメントが既定の MDX スクリプトに存在します。  
  
 既定の MDX スクリプトの中のスクリプト コマンド、名前付きセット、および計算されるメンバーの順番は、キューブ デザイナーの **[計算]** タブを使って制御できます。 既定の MDX スクリプトに格納されている計算の定義の詳細については、「 [多次元モデルの計算](../../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)」を参照してください。  
  
 関連付けられている MDX スクリプトがない場合、キューブは既定の MDX スクリプトを使用します。 キューブには最低 1 つの MDX スクリプトを関連付ける必要があります。これは、キューブが計算の動作を決定するにあたって MDX スクリプトに依存しているためです。 つまり、キューブが MDX スクリプトに関連付けられていない場合、または関連付けられている MDX が空の場合、そのキューブはセルの計算がまったくできないことになります。 Analysis Services Scripting Language (ASSL) コマンドまたは分析管理オブジェクト (AMO) のいずれかを使用してプログラム的にキューブを作成する場合は、単一の CALCULATE ステートメントが入った既定の MDX スクリプトをキューブのために作成することをお勧めします。  
  
## <a name="mdx-script-content"></a>MDX スクリプトの内容  
 MDX スクリプトには以下のステートメントと式を入れることができます。  
  
 すべての MDX スクリプト ステートメント  
 MDX スクリプトにおいて、MDX スクリプト ステートメントは、計算のコンテキストと範囲を制御し、MDX スクリプト内の他のステートメントの動作を管理します。 このカテゴリには以下のステートメントが含まれます。  
  
-   [計算](../../../mdx/mdx-scripting-calculate.md)  
  
-   [固定](../../../mdx/mdx-scripting-freeze.md)  
  
-   [スコープ](../../../mdx/mdx-scripting-scope.md)  
  
 MDX スクリプト ステートメントの詳細については、「[MDX スクリプト ステートメント &#40;MDX&#41;](../../../mdx/mdx-scripting-statements-mdx.md)」を参照してください。  
  
 [メンバーを作成します。](../../../mdx/mdx-data-definition-create-member.md)  
 CREATE MEMBER ステートメントは、計算されるメンバーを作成します。 計算されるメンバーの作成方法の詳細については、「[MDX での計算されるメンバーの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md)」を参照してください。  
  
 [セットを作成します。](../../../mdx/mdx-data-definition-create-set.md)  
 CREATE SET ステートメントは名前付きセットを作成します。 名前付きセットの作成方法の詳細については、「[MDX での名前付きセットの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md)」を参照してください。  
  
 条件ステートメント  
 条件ステートメントは、MDX スクリプトに条件ロジックを追加します。 このカテゴリには [CASE](../../../mdx/case-statement-mdx.md) および [IF](../../../mdx/mdx-scripting-if.md) ステートメントが含まれます。  
  
 代入式  
 代入式は、制約されたサブキューブに式 (値など) を代入します。 制約されたサブキューブ式は、MDX スクリプト内でサブキューブの "境界" を定義する、制約されたセット式の集合です。 以下のコードに、制約されたサブキューブ式の構文を示します。  
  
```  
<Constrained subcube> ::= (   
    ( <Constrained set> [<Crossjoin operator> <Constrained set>...] |  
    <ROOT function> |  
    <TREE function> |  
    LEAVES() |  
    * ) [, <Constrained subcube>...]  
<Constrained set> ::=   
    <Natural hierarchy>.MEMBERS |   
    <Natural hierarchy>.LEVEL(<numeric expression>).MEMBERS |   
    { <Natural hierarchy member> } |   
    DESCENDANTS( <Natural hierarchy member>, <Level expression>, ( SELF | AFTER | SELF_AND_AFTER ) ) |   
    DESCENDANTS( <Natural hierarchy member>, , LEAVES )  
<Natural hierarchy> ::= <Hierarchy identifier>  
<Natural hierarchy member> ::= <Natural hierarchy>.<identifier>[.<identifier>...]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 言語リファレンス &#40;です。MDX と #41 です。](../../../mdx/mdx-language-reference-mdx.md)   
 [MDX スクリプティングの基礎と #40 です。Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)  
  
  
