---
title: "sys.trace_categories (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
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
- trace_categories
- trace_categories_TSQL
- sys.trace_categories
- sys.trace_categories_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_categories catalog view
ms.assetid: f6a86766-e2a9-4d9f-a073-1b59e888ba7d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ece89c2798d35648e4d247ab3a56e19101341027
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="systracecategories-transact-sql"></a>sys.trace_categories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  類似したイベント クラスは、同じカテゴリに分類されます。 内の行ごと、 **sys.trace_categories**カタログ ビューは、サーバーの間で一意であるカテゴリを識別します。 これらのカテゴリが指定したバージョンは変更しないでください、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]です。  
  
 サポートされているトレース イベントの一覧については、次を参照してください。 [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)です。  
  
> **重要:** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]拡張イベント カタログ ビューを代わりに使用します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**smallint**|カテゴリの一意 ID。 この列にではまた、 **sys.trace_events**カタログ ビューです。|  
|**name**|**nvarchar(128)**|カテゴリの一意な名前。 このパラメーターはローカライズされません。|  
|**type**|**tinyint**|カテゴリの種類:<br /><br /> 0 = 標準<br /><br /> 1 = 接続<br /><br /> 2 = エラー|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.traces &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys.trace_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys.trace_events &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys.trace_event_bindings &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys.trace_subclass_values &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
