---
title: "-(コメント) (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
dev_langs:
- kbMDX
helpviewer_keywords:
- commenting characters
- -- (comment character)
ms.assetid: 02aec133-6809-4829-b9a2-102c376e21da
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 720b1d7c90e65dbfdd365e5cabf5368e27da7ef8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="comment---mdx-operator-reference"></a>コメントの MDX 演算子リファレンス
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザーが指定したコメントのテキストを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>解説  
 コメントは、別個の行として挿入することも、多次元式 (MDX) スクリプトの行の末尾で入れ子にすることも、MDX ステートメント内で入れ子にすることも可能です。 サーバーはコメントを評価しません。  
  
 1 行のコメントまたは入れ子にしたコメントには、この演算子を使用します。 -- によって挿入するコメントは、改行文字で区切ります。  
  
 コメントの長さには制限がありません。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を以下に示します。  
  
```  
-- This member returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM -- Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>参照  
 [コメント & #40 です。MDX と #41 です。](../mdx/comment-mdx.md)   
 [& #40 です。コメント &#41;& #40 です。MDX と #41 です。](../mdx/comment-mdx-double-slash.md)   
 [MDX 演算子リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)  
  
  
