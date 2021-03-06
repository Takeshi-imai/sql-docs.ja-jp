---
title: "sys.dm_fts_semantic_similarity_population (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_fts_semantic_similarity_population_TSQL
- sys.dm_fts_semantic_similarity_population
- dm_fts_semantic_similarity_population
- sys.dm_fts_semantic_similarity_population_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_semantic_similarity_population dynamic management view
ms.assetid: 33666f28-c370-47e2-a932-190316ed5f69
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a3ad5ff1a253c702f28f73e8b3e684e716e90bb9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmftssemanticsimilaritypopulation-transact-sql"></a>sys.dm_fts_semantic_similarity_population (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  関連付けられたセマンティック インデックスを持つ各テーブルの類似性インデックスごとに、ドキュメント類似性インデックスの作成に関する 1 行の状態情報を返します。  
  
 作成の処理は、抽出の処理に続いて行われます。 類似性の抽出のステップに関する状態情報については、次を参照してください。 [sys.dm_fts_index_population &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)。  
    
||||  
|-|-|-|  
|**列名**|**型**|**Description**|  
|**database_id**|**int**|作成中のフルテキスト インデックスを含むデータベースの ID。|  
|**catalog_id**|**int**|フルテキスト インデックスを含む、フルテキスト カタログの ID。|  
|**table_id**|**int**|フルテキスト インデックスを設定しているテーブルの ID。|  
|**document_count**|**int**|作成時の総ドキュメント数。|  
|**document_processed_count**|**int**|この作成サイクルの開始以降に処理されたドキュメントの数。|  
|**completion_type**|**int**|設定の完了の状態。|  
|**completion_type_description**|**nvarchar(120)**|完了の種類の説明。|  
|**worker_count**|**int**|類似性の抽出に関連付けられているワーカー スレッドの数。|  
|**ステータス**|**int**|設定の状態。 注 : 状態によっては、一時的なものもあります。 次のいずれかです。<br /><br /> 3 = 開始<br /><br /> 5 = 正常に処理中<br /><br /> 7 = 処理を停止<br /><br /> 11 = 作成が中止されました|  
|**status_description**|**nvarchar(120)**|作成の状態の説明。|  
|**start_time**|**datetime**|設定を開始した時刻。|  
|**incremental_timestamp**|**timestamp**|完全設定の開始タイムスタンプ。 他の作成の種類の場合、この値は作成の進行状況を表す、最後にコミットされたチェックポイントの値になります。|  
  
## <a name="general-remarks"></a>全般的な解説  
 詳細については、次を参照してください。[モニター セマンティック検索の管理と](../../relational-databases/search/manage-and-monitor-semantic-search.md)です。  
  
## <a name="metadata"></a>メタデータ  
 セマンティック インデックス作成のステータスに関する詳細については、クエリ[sys.dm_fts_index_population &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、関連付けられたセマンティック インデックスを持つすべてのテーブルに関するドキュメント類似性インデックスの作成状態を照会する方法を示しています。  
  
```  
SELECT * FROM sys.dm_fts_semantic_similarity_population;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セマンティクス検索の管理および監視](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
