---
title: "Database Suspect Data Page イベント クラス | Microsoft Docs"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: event-classes
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event notifications [SQL Server], database mirroring
- suspect_pages system table
- database mirroring [SQL Server], event notifications
- Database Suspect Data Page event class
ms.assetid: 098e1443-a8a0-425c-9311-0a479b1370ed
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eb75bd05b77432f1ca68294bca96e79820f7642e
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="database-suspect-data-page-event-class"></a>Database Suspect Data Page イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
**Database Suspect Data Page** イベント クラスは、 [msdb](../../relational-databases/system-tables/suspect-pages-transact-sql.md) の [suspect_pages](../../relational-databases/databases/msdb-database.md)テーブルにページがいつ追加されたかを示します。 このイベント クラスは、問題があると思われるページの発生を監視するトレースに含めます。  
  
> [!NOTE]  
>  このイベントは、 **suspect_pages** テーブルへの対応する行の挿入とは非同期に発行されます。 したがって、このイベントを受信待ちするジョブでは、対応する **suspect_pages** エントリを直ちに見つけることができない場合があります。  
  
 **Database Suspect Data Page** イベント クラスをトレースに含めても、相対的なオーバーヘッドは低くなります。 問題があると思われるページ数が増えた場合 (ディスク ドライブで問題が発生した場合など) はオーバーヘッドが大きくなる可能性があります。  
  
## <a name="database-suspect-data-page-event-class-data-columns"></a>Database Suspect Data Page イベント クラスのデータ列  
  
|データ列名|データ型|Description|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|問題があると思われるページのイベントが発生したデータベースの ID。 これは **suspect_pages** テーブルの **database_id** 列と同じです。|3|はい|  
|**EventClass**|**int**|イベントの種類は 213 です。|27|いいえ|  
|**EventSequence**|**int**|バッチ内のイベント クラスのシーケンス。|51|いいえ|  
|**SPID**|**int**|問題があると思われるページが発生した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] タスクの ID。|12|はい|  
|**StartTime**|**datetime**|イベントが発生した時刻。|14|はい|  
|**Exchange Spill**|**int**|問題があると思われるページを格納しているデータベース ファイルの ID。 これは **suspect_pages** テーブルの **file_id** 列と同じです。|22|はい|  
|**ObjectID2**|**int**|ファイル内の問題があると思われるページの ID。 これは **suspect_pages** テーブルの **page_id** 列と同じです。|56|はい|  
|**[エラー]**|**int**|発生したエラーの種類。 この値は、 **suspect_pages** テーブルのページの **event_type** 値と同じです。|31|はい|  
  
## <a name="see-also"></a>参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [suspect_pages テーブルの管理 &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
