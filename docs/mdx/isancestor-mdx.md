---
title: "IsAncestor (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ISANCESTOR
dev_langs: kbMDX
helpviewer_keywords: IsAncestor function
ms.assetid: 49d2fcdf-8d9a-4c79-bd00-4910ea149141
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2f8b226312442d5fc7b287781a505af410f050db
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="isancestor-mdx"></a>IsAncestor (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたメンバーが指定された別のメンバーの先祖かどうかを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression1*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Member_Expression2*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>Remarks  
 **IsAncestor**関数が返される**true**番目のメンバーが指定された 2 つ目のメンバーの先祖である場合。 関数を返しますそれ以外の場合、 **false**です。  
  
## <a name="example"></a>例  
 次の例を返します**true**場合 [Date] です [。Fiscal] です。CurrentMember では、2003 年 1 月の先祖を示します。  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [先祖と #40 です。MDX と #41 です。](../mdx/ancestor-mdx.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
