---
title: "空の値の操作 |Microsoft ドキュメント"
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
dev_langs: kbMDX
helpviewer_keywords:
- expressions [MDX], empty values
- empty values [MDX]
ms.assetid: 6338fb85-f513-4c3e-a774-4fd7c6986a91
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 37b91bc83640a10c9905726fdabb49c7816d77a1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="working-with-empty-values"></a>空の値の操作
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  空の値は、特定のメンバー、組、またはセルが空であることを示します。 空のセル値は、指定されたセルのデータが基になるファクト テーブルに見つからないこと、あるいは指定されたセルの組の表すメンバーの組み合わせをキューブに適用できないことのいずれかを示します。  
  
> [!NOTE]  
>  空の値は 0 の値とは異なりますが、ほとんどの場合に 0 として扱われます。  
  
 次のクエリでは、空の値と 0 の動作を示しています。  
  
```  
WITH  
//A calculated Product Category that always returns 0  
MEMBER [Product].[Category].[All Products].ReturnZero AS 0  
//Will return true for any null value  
MEMBER MEASURES.ISEMPTYDemo AS ISEMPTY([Measures].[Internet Tax Amount])  
//Will true for any null or zero value  
//To be clear: the expression 0=null always returns true in MDX  
MEMBER MEASURES.IsZero AS [Measures].[Internet Tax Amount]=0  
SELECT  
{[Measures].[Internet Tax Amount],MEASURES.ISEMPTYDemo,MEASURES.IsZero}  
ON COLUMNS,  
[Product].[Category].[Category].ALLMEMBERS  
ON ROWS  
FROM [Adventure Works]  
WHERE([Date].[Calendar].[Calendar Year].&[2001])  
```  
  
 空の値には以下の情報が当てはまります。  
  
-   [IsEmpty](../mdx/isempty-mdx.md)関数が返される**TRUE**場合にだけ、この関数で指定された組で識別されるセルが空です。 関数を返しますそれ以外の場合、 **FALSE**です。  
  
    > [!NOTE]  
    >  **IsEmpty**関数では、メンバー式が null 値を返すかどうかを判断できません。 Null のメンバーが式から返されるかどうかを判断するのには、使用、 [IS](../mdx/is-mdx.md)演算子。  
  
-   空のセル値が数値演算子 (+、-、*、/) のいずれかのオペランドである場合、もう一方のオペランドが空でない値であるなら、空のセル値は 0 として扱われます。 オペランドが両方とも空なら、数値演算子は空のセル値を返します。  
  
-   空のセル値が文字列連結演算子 (+) のオペランドである場合、もう一方のオペランドが空でない値であるなら、空のセル値は空の文字列として扱われます。 オペランドが両方とも空なら、文字列連結演算子は空のセル値を返します。  
  
-   空のセル値が比較演算子 (=、 <>、> =、 \<=、>、<)、空のセル値が 0 として扱われますまたはもう一方のオペランドのデータを入力するかどうかに応じて、空の文字列は数値または文字列では、それぞれします。 オペランドが両方とも空なら、どちらも 0 として扱われます。  
  
-   数値を照合する場合、空のセル値の照合順序は、0 と同じ位置になります。 空のセル値と 0 との照合の場合、空のセル値の照合順序は、0 の前になります。  
  
-   文字列の値を照合する場合、空のセル値の照合順序は、空の文字列と同じ位置になります。 空のセル値と空の文字列との照合の場合、空のセル値の照合順序は、空の文字列の前になります。  
  
## <a name="dealing-with-empty-values-in-mdx-statements-and-cubes"></a>MDX ステートメントおよびキューブにおける空の値の処理  
 多次元式 (MDX) ステートメントでは、空の値を探してから、有効な (空でない) データの入ったセルに対して計算を実行することができます。 計算時に空の値を除去することが必要な場合があります。平均値などの計算では、空のセル値が含まれていると正確な結果を得ることができません。  
  
 空の値が基になるファクト テーブル データに格納されると、既定では、キューブが処理される際にこの値が 0 に変換されます。 使用することができます、 **Null 処理**オプションを制御するメジャーを null のファクトが 0 に変換されるかどうかに変換空の値、またはでも例外をスロー エラーの処理中にします。 空のセル値がクエリ結果に表示されないようにするには、空の値を除去するか他の値に置き換えるクエリ、計算されるメンバー、または MDX スクリプト ステートメントを作成する必要があります。  
  
 クエリから空の行や列を削除するには、軸セットの定義の前に NON EMPTY ステートメントを使用できます。 たとえば、次のクエリでは、製品カテゴリ Bikes のみが返されます。これは、2001 年に販売された唯一のカテゴリであるためです。  
  
 `SELECT`  
  
 `{[Measures].[Internet Tax Amount]}`  
  
 `ON COLUMNS,`  
  
 `//Comment out the following line to display all the empty rows for other Categories`  
  
 `NON EMPTY`  
  
 `[Product].[Category].[Category].MEMBERS`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Date].[Calendar].[Calendar Year].&[2001])`  
  
 セットから空の組を削除するには、NonEmpty 関数を使用する方法がより一般的です。 次のクエリでは、2 つの計算されるメジャーを示しています。1 つは、製品カテゴリの数をカウントし、もう 1 つは、[Internet Tax Amount] メジャーと 2001 年の値を持つ製品カテゴリの数を示します。  
  
 `WITH`  
  
 `MEMBER MEASURES.CategoryCount AS`  
  
 `COUNT([Product].[Category].[Category].MEMBERS)`  
  
 `MEMBER MEASURES.NonEmptyCategoryCountFor2001 AS`  
  
 `COUNT(`  
  
 `NONEMPTY(`  
  
 `[Product].[Category].[Category].MEMBERS`  
  
 `,([Date].[Calendar].[Calendar Year].&[2001], [Measures].[Internet Tax Amount])`  
  
 `))`  
  
 `SELECT`  
  
 `{MEASURES.CategoryCount,MEASURES.NonEmptyCategoryCountFor2001 }`  
  
 `ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 詳細については、次を参照してください。 [NonEmpty &#40;です。MDX と #41 です](../mdx/nonempty-mdx.md)。  
  
## <a name="empty-values-and-comparison-operators"></a>空の値と比較演算子  
 データに空の値がある場合、論理演算子と比較演算子は、TRUE または FALSE ではなく EMPTY を返すことがあります。 このように 3 つの値を生成する論理は、アプリケーション エラーの原因になります。 次の表は、空の値の比較を採用した場合の結果を示しています。  
  
 下の表は、AND 演算子を 2 つのブール値オペランドに適用した結果を示します。  
  
|[AND]|TRUE|EMPTY|FALSE|  
|---------|----------|-----------|-----------|  
|**場合は TRUE。**|TRUE|FALSE|FALSE|  
|**空**|FALSE|EMPTY|FALSE|  
|**FALSE**|FALSE|FALSE|FALSE|  
  
 下の表は、OR 演算子を 2 つのブール値オペランドに適用した結果を示します。  
  
|スイッチまたは|TRUE|FALSE|  
|--------|----------|-----------|  
|**場合は TRUE。**|TRUE|TRUE|  
|**空**|TRUE|TRUE|  
|**FALSE**|TRUE|FALSE|  
  
 下の表は、NOT 演算子が論理演算子の結果を否定または逆転するようすを示します。  
  
|NOT 演算子が適用されるブール式|評価結果|  
|-------------------------------------------------------------|------------------|  
|TRUE|FALSE|  
|EMPTY|EMPTY|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です](../mdx/mdx-function-reference-mdx.md)   
 [MDX 演算子リファレンス &#40;です。MDX と #41 です](../mdx/mdx-operator-reference-mdx.md)   
 [式 &#40;です。MDX と #41 です](../mdx/expressions-mdx.md)  
  
  
