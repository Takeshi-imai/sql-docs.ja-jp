---
title: "MSmerge_identity_range_allocations (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_identity_range_allocations
- MSmerge_identity_range_allocations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range_allocations system table
ms.assetid: 6362e35e-0ab3-4638-855b-1ce013f5fd6d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ad5ad628c5f839c64d88c54e777aca7e0bc52b7e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msmergeidentityrangeallocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_identity_range_allocations** id 範囲の割り当て、パブリッシャーとサブスクライバーの両方にパブリッシュされたアーティクルの履歴を追跡するためにテーブルを使用します。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id などがあります。**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**nvarchar (128)**|パブリケーション データベースの名前です。|  
|**パブリケーション**|**nvarchar (128)**|パブリケーションの名前を指定します。|  
|**アーティクル**|**nvarchar (128)**|アーティクルの名前です。|  
|**サブスクライバー**|**nvarchar (128)**|サブスクライバーの名前。|  
|**@subscriber_db**|**nvarchar (128)**|サブスクリプション データベースの名前。|  
|**is_pub_range**|**bit**|ID 範囲がパブリッシャーに割り当てられているかどうかの一覧です。|  
|**ranges_allocated**|**tinyint**|割り当てられている ID 範囲の数です。|  
|**range_begin**|**numeric(38)**|範囲の開始値です。|  
|**range_end**|**numeric(38)**|範囲の最後の値です。|  
|**next_range_begin**|**numeric(38)**|次の範囲で割り当てられる開始値です。|  
|**next_range_end**|**numeric(38)**|次の範囲で割り当てられる最後の値です。|  
|**max_used**|**numeric(38)**|使用されている最大 ID 値です。|  
|**time_of_allocation**|**datetime**|割り当てが行われた時刻です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
