---
title: "DROP CELL CALCULATION ステートメント (MDX) |Microsoft ドキュメント"
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
f1_keywords:
- Calculation
- DROP
- DROP_CELL_CALCULATION
- CELL CALCULATION
- DROP CELL
- cell
- DROP CELL CALCULATION
dev_langs: kbMDX
helpviewer_keywords:
- deleting calculations
- dropping calculations
- removing calculations
- DROP CELL CALCULATION statement
- calculations [SQL Server]
- cubes [Analysis Services], calculations
ms.assetid: 77caedf4-dd96-4eac-a5e4-fd82148a44a7
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e84207fc0354c7599feb823f0b54b27fdc164619
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-definition---drop-cell-calculation"></a>MDX データ定義の DROP CELL CALCULATION
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたセル計算を削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP [ SESSION ] CELL CALCULATION CURRENTCUBE | Cube_Name.CellCalc_Name  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブ式の名前を指定する有効な文字列式です。  
  
 *CellCalc_Name*  
 削除するセル計算の名前を指定する有効な文字列式です。  
  
## <a name="see-also"></a>参照  
 [CELL CALCULATION ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-cell-calculation.md)   
 [MDX データ定義ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
