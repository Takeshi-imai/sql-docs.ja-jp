---
title: "STInteriorRingN (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7335cdeab403eb8530a7a26742c7c0d715dce0a1
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

指定した内部リングを返す、 **Polygongeometry**インスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 **Int** 1 ~ 内部リングの数の式、 **geometry**インスタンス。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
 Open Geospatial Consortium (OGC) の型: **LineString**  
  
## <a name="remarks"></a>解説  
 このメソッドが戻る**null**場合、 **geometry**インスタンスが多角形ではありません。 このメソッドはスローされても、 **ArgumentOutOfRangeException**式がリングの数よりも大きい場合。 使用してリングの数を返すことが`STNumInteriorRing``()`です。  
  
## <a name="examples"></a>使用例  
 次の例を作成、`Polygon`使用して、インスタンス`STInteriorRingN()`として多角形の内部リングを返す、 **LineString**です。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

