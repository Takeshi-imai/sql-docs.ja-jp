---
title: "sys.partition_range_values (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sys.partition_range_values
- partition_range_values_TSQL
- partition_range_values
- sys.partition_range_values_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partition_range_values catalog view
ms.assetid: 9aee483e-61f3-4613-bec6-f084161f45ac
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0f1fd5ab82c373dbc08edf7a901ccfee4d6eed34
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syspartitionrangevalues-transact-sql"></a>sys.partition_range_values (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  タイプ R のパーティション関数の範囲境界値ごとに 1 行のデータを保持します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**function_id**|**int**|この範囲境界値のパーティション関数の ID です。|  
|**boundary_id**|**int**|左端の境界が ID 1 で始まる境界値の組の ID (1 から始まる序数) です。|  
|**parameter_id**|**int**|この値が対応する関数のパラメーターの ID です。 この列の値でそれらに対応して、 **parameter_id**の列、 **sys.partition_parameters**カタログ ビューの特定の**function_id**です。|  
|**値**|**sql_variant**|実際の境界値です。|  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [パーティション関数のカタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.partition_functions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_parameters &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)  
  
  
