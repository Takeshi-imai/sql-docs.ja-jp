---
title: "STCurveToLine (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STCurveToLine_TSQL
- STCurveToLine
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveToLine method (geography)
ms.assetid: 2f863a85-6168-465a-b32f-bb5e3de58dee
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9d2ad93d8bc292ebb86233917dc3f934fbe57dca
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stcurvetoline-geography-data-type"></a>STCurveToLine (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  多角形近似を返します、 **geography**の円弧セグメントを格納しているインスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STCurveToLine()  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 返します、 **LineString**インスタンスの場合、 **CircularString**または**CompoundCurve**インスタンス。  
  
 返します、**多角形**インスタンスの場合、 **CurvePolygon**インスタンス。  
  
 コピーを返す**geography**を含まないインスタンス**CircularString**、 **CompoundCurve**、または**CurvePolygon**インスタンス。  
  
 は、SQL MM 仕様とは異なり、このメソッドは多角形近似の計算に z 座標値を使用しません。 呼び出し元に存在する任意の z 座標値**geography**インスタンスは無視されます。  
  
## <a name="examples"></a>使用例  
 次の例は、`LineString` インスタンスの多角形近似である `CircularString` インスタンスを返します。  
  
 `DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';`  
  
 `DECLARE @g2 geography;`  
  
 `SET @g2 = @g1.STCurveToLine();`  
  
 `SELECT @g1.STNumPoints() AS G1, @g2.STNumPoints() AS G2;`  
  
## <a name="see-also"></a>参照  
 [STLength (&) #40";"geography データ型"&"#41;](../../t-sql/spatial-geography/stlength-geography-data-type.md)   
 [STNumPoints (&) #40";"geography データ型"&"#41;](../../t-sql/spatial-geography/stnumpoints-geography-data-type.md)   
 [空間データ型の概要](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  