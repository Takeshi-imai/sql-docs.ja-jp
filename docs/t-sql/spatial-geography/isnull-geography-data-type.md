---
title: "IsNull (geography データ型) |Microsoft ドキュメント"
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
- IsNull (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull method
ms.assetid: c031074f-bfda-4584-a3bf-4e7c324f237f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c07ddb41209c507845da7e790035ab54ed1044f1
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="isnull-geography-data-type"></a>IsNull (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  場合を指定するプロパティ、 **geography**インスタンスが null です。 インスタンスが NULL の場合は "TRUE" を、NULL ではない場合は 0 を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.IsNull  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型:**ビット**  
  
 CLR 型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 `IsNull`テストに使用できるかどうか、 **geography**インスタンスが null です。 このテストの結果は若干複雑であるため注意してください。インスタンスが NULL でなければ 0 を返し、インスタンスが NULL であれば NULL を返します。  
  
 このメソッドは、主に使用、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インフラストラクチャをテストする T-SQL 述語の IS NULL を使用することをお勧めするかどうか、 **geography**インスタンスが null です。 T-SQL ステートメントの詳細については、IS NULL 述語は、「 [IS NULL と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/is-null-transact-sql.md).  
  
## <a name="examples"></a>使用例  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
