---
title: "dbo.cdc_jobs (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- cdc_jobs
- cdc_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.cdc_jobs
ms.assetid: 85e2d580-1c54-4b81-b7e6-2e12997199fd
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1c455f083d0cb635d62e67a9b8e03e7bdda0b106
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="dbocdcjobs-transact-sql"></a>dbo.cdc_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キャプチャ ジョブおよびクリーンアップ ジョブで使用される、変更データ キャプチャの構成パラメーターを格納します。 このテーブルが格納されている**msdb**です。  
  
 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ジョブが実行されるデータベースの ID。|  
|**job_type**|**nvarchar (20)**|ジョブの種類 ('capture' または 'cleanup')。|  
|**job_id**|**uniqueidentifier**|ジョブに関連付けられた一意の ID。|  
|**maxtrans**|**int**|各スキャン サイクルで処理する最大トランザクション数。<br /><br /> **maxtrans**はキャプチャ ジョブでのみ有効です。|  
|**maxscans**|**int**|ログからすべての行を抽出するために実行する最大スキャン サイクル数。<br /><br /> **maxscans**はキャプチャ ジョブでのみ有効です。|  
|**継続的です**|**bit**|キャプチャ ジョブを連続的に実行するか (1)、1 回だけ実行するか (0) を示すフラグ。 詳細については、次を参照してください。 [sys.sp_cdc_add_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **継続的な**はキャプチャ ジョブでのみ有効です。|  
|**pollinginterval**|**bigint**|ログ スキャン サイクル間の秒数。<br /><br /> **pollinginterval**はキャプチャ ジョブでのみ有効です。|  
|**保有期間**|**bigint**|変更行が変更テーブルに保持される分数。<br /><br /> **保有期間**はクリーンアップ ジョブでのみ有効です。|  
|**しきい値**|**bigint**|クリーンアップ時に 1 つのステートメントを使用して削除できる最大削除エントリ数。|  
  
## <a name="see-also"></a>参照  
 [sys.sp_cdc_add_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)   
 [sys.sp_cdc_change_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)   
 [sys.sp_cdc_help_jobs &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)   
 [sys.sp_cdc_drop_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql.md)  
  
  
