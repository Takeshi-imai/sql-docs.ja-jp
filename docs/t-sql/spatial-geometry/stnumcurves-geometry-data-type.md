---
title: "STNumCurves (geometry データ型) |Microsoft ドキュメント"
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
dev_langs:
- TSQL
helpviewer_keywords:
- STNumCurves method (geometry)
ms.assetid: 20c2fa0b-656b-4519-b34c-cc8f094290d4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 92cf7af65b64c412aff37311ccf1e9b44484968b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="stnumcurves-geometry-data-type"></a>STNumCurves (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

このメソッド内の曲線の数を返します、 **geometry**インスタンス、インスタンスが 1 次元の空間データ型の場合。 1 次元の空間データ型は**LineString**、 **CircularString**、および**CompoundCurve**です。 `STNumCurves`() は単純型に対してのみ機能します。は機能しません**geometry**コレクションと同様に**MultiLineString**です。
  
## <a name="syntax"></a>構文  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>解説  
 空の 1 次元**geometry**インスタンスは 0 を返します。 **NULL**ときに返される、 **geometry**インスタンスは 1 次元のインスタンスまたは初期化されていません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>A. CircularString インスタンスに対して STNumCurves() を使用する  
 次の例では、`CircularString` インスタンスに含まれる曲線の数を取得する方法を示します。  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)');  
 SELECT @g.STNumCurves();
 ```  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>B. CompoundCurve インスタンスに対して STNumCurves() を使用する  
 次の例で`STNumCurves()`内の曲線の数を返す、`CompoundCurve`インスタンス。  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))');  
 SELECT @g.STNumCurves();
 ```  
  
## <a name="see-also"></a>参照  
 [空間データ型の概要](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

