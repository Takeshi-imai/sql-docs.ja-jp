---
title: "sys.system_sql_modules (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- system_sql_modules_TSQL
- sys.system_sql_modules
- sys.system_sql_modules_TSQL
- system_sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_sql_modules catalog view
ms.assetid: ad3548bc-4780-4821-b962-b421d52daed9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 66917b2a30649119ee7921f4343d79765efbb8b1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syssystemsqlmodules-transact-sql"></a>sys.system_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  SQL 言語定義モジュールを含むシステム オブジェクトごとに 1 行のデータを返します。 FN、IF、P、PC、TF、V 型のシステム オブジェクトには、SQL モジュールが関連付けられています。 親オブジェクトを識別するためにはこのビューに参加できる[sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|モジュールを含むオブジェクトのオブジェクト識別番号。データベース内で一意です。|  
|**定義**|**nvarchar(max)**|このモジュールを定義する SQL テキスト。|  
|**uses_ansi_nulls**|**bit**|1 = モジュールは、SET ANSI_NULLS データベース オプションが ON の状態で作成されました。<br /><br /> 常に 1 を返します。|  
|**uses_quoted_identifier**|**bit**|1 = モジュールは、SET QUOTED_IDENTIFIER ON の状態で作成されました。<br /><br /> 常に 1 を返します。|  
|**is_schema_bound**|**bit**|0 = モジュールは、SCHEMABINDING オプションで作成されませんでした。<br /><br /> 常に 0 を返します。|  
|**uses_database_collation**|**bit**|0 = モジュールは、データベースの既定の照合順序に依存していません。<br /><br /> 常に 0 を返します。|  
|**is_recompiled**|**bit**|0 = プロシージャは、WITH RECOMPILE オプションを使って作成されませんでした。<br /><br /> 常に 0 を返します。|  
|**null_on_null_input**|**bit**|0 = モジュールは、NULL 入力に対して NULL 出力を生成するように作成されませんでした。<br /><br /> 常に 0 を返します。|  
|**execute_as_principal_id**|**int**|常に NULL を返します|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.all_sql_modules &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
