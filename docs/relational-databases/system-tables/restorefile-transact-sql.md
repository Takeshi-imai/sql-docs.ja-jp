---
title: "restorefile (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- restorefile
- restorefile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restorefile system table
- restoring files [SQL Server], restorefile system table
- file restores [SQL Server], restorefile system table
ms.assetid: 8e40145a-8559-4abe-8e2a-39b818928009
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e42d9d3dc2e40cefd04c9d7519e92158aed4b51
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="restorefile-transact-sql"></a>restorefile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  復元されたファイルごとに 1 行のデータを格納します。復元されたファイルには、ファイル グループ名から間接的に復元されたものも含まれます。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|対応する復元操作を特定するための一意な識別番号。 参照**restorehistory (restore_history_id)**です。|  
|**file_number**|**numeric(10,0)**|復元されたファイルのファイル識別番号。 この番号は、各データベースの中で一意であることが必要です。 NULL を指定できます。<br /><br /> データベース スナップショットの状態にデータベースを戻すとき、この値は完全な復元を行う場合と同じ方法で設定されます。|  
|**destination_phys_drive**|**nvarchar(260)**|ファイルの復元先のドライブまたはパーティション。 NULL を指定できます。<br /><br /> データベース スナップショットの状態にデータベースを戻すとき、この値は完全な復元を行う場合と同じ方法で設定されます。|  
|**destination_phys_name**|**nvarchar(260)**|ファイルの復元先のファイル名。ドライブやパーティション情報は含みません。 NULL を指定できます。<br /><br /> データベース スナップショットの状態にデータベースを戻すとき、この値は完全な復元を行う場合と同じ方法で設定されます。|  
  
## <a name="remarks"></a>解説  
 次の表では他のバックアップと履歴テーブルの行の数を減らすためには、実行、 [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)ストアド プロシージャです。  
  
## <a name="see-also"></a>参照  
 [バックアップと復元のテーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefilegroup &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [restorehistory &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/restorehistory-transact-sql.md)   
 [システム テーブルと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
