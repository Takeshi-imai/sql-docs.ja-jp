---
title: "MSsnapshotdeliveryprogress (TRANSACT-SQL) |Microsoft ドキュメント"
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
- MSsnapshotdeliveryprogress_TSQL
- MSsnapshotdeliveryprogress
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshotdeliveryprogress system table
ms.assetid: 9164bfe2-6fc4-4b52-946a-09ea3cf67041
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d7fbb80963679858339cc1df9206f101968f4f8e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssnapshotdeliveryprogress-transact-sql"></a>MSsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsnapshotdeliveryprogress**テーブルが正常に配信されたサブスクライバーにスナップショットが適用されているときにファイルを追跡するために使用します。 マージ エージェントがセッション中にすべてのファイルを配信できなかった場合に、このデータを使用してファイルの配信を再開し、次にマージ エージェントが実行されたときに同じファイルが再度配信されないようにします。 このテーブルは、サブスクライバー側でサブスクリプション データベースに格納されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**session_token**|**nvarchar (260)**|ファイルが正常に配信された配信元のスナップショット フォルダーへのパスを識別します。 パラメーター化されたフィルター文字列を使用するパブリケーションの**dynsnap**の値に追加されます。|  
|**progress_token_hash**|**int**|生成されたハッシュ値の値に基づく*progress_token*ために使用される参照の効率を向上させる、指定された*progress_token*値。|  
|**progress_token**|**nvarchar (500)**|正常に配信されたファイルを識別します。値は、ファイル名とパスの組み合わせです。|  
|**progress_timestamp**|**datetime**|**Datetime**スナップショット ファイルが正常に配信されるかを示す値。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
