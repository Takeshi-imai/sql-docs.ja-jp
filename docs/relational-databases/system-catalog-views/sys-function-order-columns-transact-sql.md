---
title: "sys.function_order_columns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- function_order_columns
- sys.function_order_columns_TSQL
- function_order_columns_TSQL
- sys.function_order_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.function_order_columns catalog view
ms.assetid: 29287973-3125-4d35-8ca9-92cb45828854
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 01973c84fe0e66709230c393d445465d17dd42b1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysfunctionordercolumns-transact-sql"></a>sys.function_order_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  列の一部であるごとに 1 行を返します、**順序**一般的な言語ランタイム (CLR) テーブル値関数の式。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|順序が定義されているオブジェクト (CLR テーブル値関数) の ID です。|  
|**order_column_id**|**int**|順序列の ID です **order_column_id**内でのみ一意では**object_id**です。<br /><br /> **order_column_id**順序付けにおけるこの列の位置を表します。|  
|**column_id**|**int**|内の列の ID **object_id**です。<br /><br /> **column_id**内でのみ一意では**object_id**です。|  
|**is_descending**|**bit**|1 = 順序列に降順の並べ替え方向が設定されています。<br /><br /> 0 = 順序列に昇順の並べ替え方向が設定されています。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
