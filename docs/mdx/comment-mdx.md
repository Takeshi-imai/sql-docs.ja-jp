---
title: "コメント (MDX) |Microsoft ドキュメント"
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
- '*/'
- /*
dev_langs:
- kbMDX
helpviewer_keywords:
- commenting characters
- /*...*/ (comment)
ms.assetid: 64434ae4-80ce-4634-86b8-4125dfaa7f61
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: fca15a526cbd5329c8116e751bda4959a46e1713
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="comment-mdx"></a>コメント (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザーが指定したコメントのテキストを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
/* Comment_Text */      
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>解説  
 サーバーが、コメント文字の間のテキストを評価できません/* と\*/です。 コメントは、別個の行に挿入することも、多次元式 (MDX) ステートメントの中に指定することも可能です。 によって複数行のコメントを示す必要があります/\*と\*/です。  
  
 コメントの長さには制限がありません。 `/* Test /*Comment*/ Text*/` のようにコメントを入れ子にすることもできます。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を以下に示します。  
  
```  
/* This member returns the gross profit margin for product types  
  and reseller types crossjoined by year. */  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM /* Select from the Adventure Works cube. */  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>参照  
 [& #40 です。コメント &#41;& #40 です。MDX と #41 です。](../mdx/comment-mdx-double-slash.md)   
 [--& #40 です。コメント &#41;& #40 です。MDX と #41 です。](../mdx/comment-mdx-operator-reference.md)   
 [MDX 演算子リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)  
  
  
