---
title: "&lt;&gt;(等しくない)(MDX) |Microsoft ドキュメント"
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
f1_keywords: <>
dev_langs: kbMDX
helpviewer_keywords:
- not equal to operator (<>)
- <> (not equal to operator)
ms.assetid: b4eb3f1c-8b68-4530-a8f3-e3b8414ac789
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6f515685f01b1795c361b38f031fa9e8d871dbb5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="ltgt-not-equal-to-mdx"></a>&lt;&gt;(等しくない)(MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  1 つの多次元式 (MDX) 式の値が、別の MDX 式の値と等しくないかどうかを判別する比較演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
MDX_Expression <> MDX_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *MDX_Expression*  
 有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 以下の条件に基づくブール値です。  
  
-   **true**両方のパラメーターが null 以外の場合と、最初のパラメーターが 2 番目のパラメーターと等しくないかどうか。  
  
-   **false**両方のパラメーターが null 以外の場合と、最初のパラメーターが 2 番目のパラメーターと等しいかどうかは。  
  
-   いずれか一方または両方のパラメーターが NULL 値に評価される場合は、NULL です。  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)  
  
  
