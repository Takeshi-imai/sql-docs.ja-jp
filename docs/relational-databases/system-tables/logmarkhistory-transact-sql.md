---
title: "logmarkhistory (TRANSACT-SQL) |Microsoft ドキュメント"
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
- logmarkhistory
- logmarkhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logmarkhistory system table
ms.assetid: 5c1becc5-f34e-4869-bf69-dfafab684540
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5d4948a79bfd4b529b87cd0f5c223e302172a26a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="logmarkhistory-transact-sql"></a>logmarkhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コミットされたマーク付きのトランザクションごとに 1 行のデータを格納します。 次の表は、 **msdb**データベース。  
  

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|マーク付きのトランザクションが発生したローカル データベース。|  
|**mark_name**|**nvarchar(128)**|マーク付きのトランザクションに指定されたユーザー定義の名前。|  
|**説明**|**nvarchar (255)**|マーク付きのトランザクションに指定されたユーザー定義の説明。 NULL を指定できます。|  
|**user_name**|**nvarchar(128)**|マーク付きのトランザクションを実行したデータベース ユーザー名。 NULL を指定できます。|  
|**lsn**|**numeric(25,0)**|マークが発生したトランザクション レコードのログ シーケンス番号。|  
|**mark_time**|**datetime**|マーク付きトランザクションのコミット時間 (ローカル時間)。|  
  
## <a name="see-also"></a>参照  
 [マークされたトランザクションへのデータベースの復元 &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)   
 [システム テーブルと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
