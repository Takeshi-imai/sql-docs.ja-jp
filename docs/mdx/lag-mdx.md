---
title: "Lag (MDX) |Microsoft ドキュメント"
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
f1_keywords: LAG
dev_langs: kbMDX
helpviewer_keywords: Lag function
ms.assetid: 08c704ea-35d8-44ee-abe5-93bd24b99906
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a219e0b8455ff3a66d20a8c670bb8675481498e4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="lag-mdx"></a>Lag (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  レベル内の指定されたメンバーより指定された数だけ後退した位置にあるメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Lag(Index)   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Index*  
 メンバー位置を後退させる数を指定する有効な数値式です。  
  
## <a name="remarks"></a>解説  
 レベル内のメンバーの位置は、属性階層の自然な順序によって決まります。 メンバーの位置の基点は 0 です。  
  
 指定した間隔が 0 の場合、 **Lag**関数は、指定されたメンバー自体を返します。  
  
 指定した間隔が負の場合、 **Lag**関数は、後続のメンバーを返します。  
  
 `Lag(1)`等価の[PrevMember](../mdx/prevmember-mdx.md)関数。 `Lag(-1)`等価の[NextMember](../mdx/nextmember-mdx.md)関数。  
  
 **Lag**関数がに似ていますが、[リード](../mdx/lead-mdx.md)関数点を除いて、**潜在顧客**関数は方向が逆になります、 **Lag**関数。 つまり、`Lag(n)`は等価`Lead(-n)`です。  
  
## <a name="example"></a>例  
 次の例では、2001 年 12 月の値が返されます。  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(2) ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、2002 年 3 月の値が返されます。  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(-1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
