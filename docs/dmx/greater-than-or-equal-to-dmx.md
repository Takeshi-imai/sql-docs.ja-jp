---
title: "&gt;= (より大きいか等しい) (DMX) |Microsoft ドキュメント"
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
ms.topic: language-reference
dev_langs: DMX
helpviewer_keywords:
- '>= (greater than or equal to operator)'
- greater than or equal to (>=)
ms.assetid: a96b7e9c-72dc-4df1-aa41-85aad933df96
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: da7383aecf422f9ebdf43fe6932610423f3a34a9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="gt-greater-than-or-equal-to-dmx"></a>&gt;= (より大きいか等しい) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  あるデータ マイニング拡張機能 (DMX) 式の値が他の DMX 式の値以上かどうかを判断する比較演算子を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DMX_Expression >= DMX_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DMX_Expression*  
 有効な DMX 式です。  
  
## <a name="return-value"></a>戻り値  
 両方のパラメーターが NULL 以外であり、1 番目のパラメーターの値が 2 番目のパラメーターの値以上の場合、TRUE を含むブール値です。 両方のパラメーターが NULL 以外であり、1 番目のパラメーターの値が 2 番目のパラメーターの値より小さい場合、FALSE を含むブール値です。 どちらかまたは両方のパラメーターの結果が NULL 値の場合、NULL 値を含むブール値です。  
  
## <a name="see-also"></a>参照  
 [比較演算子 &#40;DMX&#41;](../dmx/operators-comparison.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子 &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
