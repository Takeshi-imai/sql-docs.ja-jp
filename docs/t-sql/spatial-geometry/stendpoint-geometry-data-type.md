---
title: "STEndpoint (geometry データ型) |Microsoft ドキュメント"
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
- STEndpoint (geometry Data Type)
- STEndpoint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STEndpoint (geometry Data Type)
ms.assetid: 61773c45-b568-4e0c-94da-1310c42de7f5
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1ab1d1e533897f3042977902c2b7938dbe048e00
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="stendpoint-geometry-data-type"></a>STEndpoint (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

終点を返します、 **geometry**インスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
.STEndPoint ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
 Open Geospatial Consortium (OGC) の型:**ポイント**  
  
## <a name="remarks"></a>解説  
 `STEndPoint()`相当[STPointN](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md) (x.numpoints()) です。  
  
 このメソッドは、空で呼び出された場合は null を返します**geometry**インスタンス。  
  
## <a name="examples"></a>使用例  
 次の例を作成、`LineString`インスタンス`STGeomFromText()`を使用して`STEndpoint()`の終点を取得する、`LineString`です。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STEndPoint().ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

