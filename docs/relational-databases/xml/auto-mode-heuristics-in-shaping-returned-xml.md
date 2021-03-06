---
title: "返される XML を構造化する際の AUTO モード ヒューリスティック | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AUTO FOR XML mode, heuristics in shaping returned XML
ms.assetid: 6c5cb6c1-2921-4ba1-8100-0bf8074f9103
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d9e8dae9ee9c8ccb9690fbe434786b6c40a31b62
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="auto-mode-heuristics-in-shaping-returned-xml"></a>返される XML を構造化する際の AUTO モード ヒューリスティック
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
AUTO モードでは、返される XML の構造はクエリに基づいて決定されます。 要素を入れ子にする方法を決定するとき、AUTO モード ヒューリスティックによって、隣接する行の列値が比較されます。 **ntext**型、 **text**型、 **image**型、および **xml**型を除くすべての型の列が比較されます。 **(n)varchar(max)** 型と **varbinary(max)** 型の列は比較されます。  
  
 次の例では、生成される XML の構造を決定する AUTO モード ヒューリスティックを示します。  
  
```  
SELECT T1.Id, T2.Id, T1.Name  
FROM   T1, T2  
WHERE ...  
FOR XML AUTO  
ORDER BY T1.Id  
```  
  
 テーブル T1 のキーが指定されていない場合は、新しい <`T1`> 要素の開始位置を決定するために、**ntext** 型、**text** 型、**image** 型、および **xml** 型を除く T1 の列のすべての値が比較されます。 次に、**Name** 列が **nvarchar(40)** 型で、SELECT ステートメントから次の行セットが返されるとします。  
  
```  
T1.Id  T1.Name  T2.Id  
-----------------------  
1       Andrew    2  
1       Andrew    3  
1       Nancy     4  
```  
  
 AUTO モード ヒューリスティックにより、テーブル T1 のすべての値 (Id 列と Name 列) が比較されます。 最初の 2 行の Id 列と Name 列の値は同じなので、2 つの \<T2> 子要素を持っている 1 つの \<T1> 要素が結果に追加されます。  
  
 次に、返される XML を示します。  
  
```  
<T1 Id="1" Name="Andrew">  
    <T2 Id="2" />  
    <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
      <T2 Id="4" />  
</T>  
```  
  
 ここで、Name 列は **text** 型であるとします。 この型の値は、AUTO モード ヒューリスティックによって比較されません。 この場合、値が異なると想定されます。 この結果、次に示すように XML が生成されます。  
  
```  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="2" />  
</T1>  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
  <T2 Id="4" />  
</T1>  
```  
  
## <a name="see-also"></a>参照  
 [FOR XML での AUTO モードの使用](../../relational-databases/xml/use-auto-mode-with-for-xml.md)  
  
  
