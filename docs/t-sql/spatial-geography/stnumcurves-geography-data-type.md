---
title: "STNumCurves (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- STNumCurves
- STNumCurves_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumCurves method (geography)
ms.assetid: e98a56c2-8496-4dfd-9b37-7f3c4ca9b2b5
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7baccab2b0087fdb2ae90f5b212b4d820919d25
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="stnumcurves-geography-data-type"></a>STNumCurves (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  1 次元内の曲線の数を返します**geography**インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 1 次元の空間データ型は**LineString**、 **CircularString**、および**CompoundCurve**です。 空の 1 次元**geography**インスタンスは 0 を返します。  
  
 `STNumCurves`() は単純型に対してのみ機能します。は機能しません**geography**コレクションと同様に**MultiLineString**です。 **NULL**ときに返される、 **geography**インスタンスが 1 次元のデータ型ではありません。  
  
 **Null**初期化されていないに返される**geography**インスタンス。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>A. CircularString インスタンスに対して STNumCurves() を使用する  
 次の例では、`CircularString` インスタンスに含まれる曲線の数を取得する方法を示します。  
  
```
 DECLARE @g geography; 
 SET @g = geography::Parse('CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 SELECT @g.STNumCurves();
 ```  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>B. CompoundCurve インスタンスに対して STNumCurves() を使用する  
 次の例で`STNumCurves()`内の曲線の数を返す、`CompoundCurve`インスタンス。  
  
```
 DECLARE @g geography;  
 SET @g = geography::Parse('COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))');  
 SELECT @g.STNumCurves();
 ```  
  
## <a name="see-also"></a>参照  
 [空間データ型の概要](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
