---
title: "sys.dm_exec_distributed_request_steps (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_distributed_request_steps
- sys.dm_exec_distributed_request_steps management view
ms.assetid: 1954541d-b716-4e03-8fcc-7022f428e01d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 348b78de034f252f5ea9561df53dc69c267d8257
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecdistributedrequeststeps-transact-sql"></a>sys.dm_exec_distributed_request_steps (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  指定の PolyBase 要求またはクエリを構成するすべてのステップに関する情報を保持します。 これには、クエリのステップごとに 1 行が一覧表示します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**int**|execution_id と step_index は、このビューのキーを構成します。 要求に関連付けられている一意の数値 id です。|内の ID を参照してください[sys.dm_exec_requests &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)。|  
|step_index|**int**|この手順の要求を構成する手順のシーケンス内の位置。|ステップを含む要求に対して (n 1) に 0 を返します。|  
|operation_type|**nvarchar(128)**|この手順で表される操作の種類。|'MoveOperation'、'OnOperation'、'RandomIDOperation'、'RemoteOperation'、'ReturnOperation'、'ShuffleMoveOperation'、'TempTablePropertiesOperation'、'DropDiagnosticsNotifyOperation'、'HadoopShuffleOperation'、'HadoopBroadCastOperation'、'HadoopRoundRobinOperation'|  
|distribution_type|**nvarchar(32)**|手順を実行しています。|'AllComputeNodes'、' AllDistributions'、'ComputeNode'、'配布'、'AllNodes'、'SubsetNodes'、'SubsetDistributions'、' 指定されていない' です。|  
|location_type|**nvarchar(32)**|手順を実行しています。|'Compute'、'ヘッド' または 'DMS' です。 すべてのデータ移動の手順では、'DMS' を示しています。|  
|ステータス|**nvarchar(32)**|この手順の状態|'Pending'、'Running'、'完了'、'失敗'、'UndoFailed'、'PendingCancel'、' が取り消されました '、'を元に戻す'、'中止'|  
|error_id|**nvarchar(36)**|存在する場合は、このステップに関連付けられているエラーの一意の id|Id を参照してください[sys.dm_exec_compute_node_errors &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md)エラーが発生しなかった場合は NULL です。|  
|start_time|**datetime**|ステップの実行開始時刻|小さいまたは現在の時刻と等しい、大きいか等しい end_compile_time が、この手順が属している、クエリのです。|  
|end_time|**datetime**|このステップ実行を完了したが取り消された場合、または失敗したの時間です。|小さいまたは現在の時刻に等しいと大きいか等しい start_time、手順については、現在実行中に NULL を設定するか、キューに登録します。|  
|total_elapsed_time|**int**|クエリのステップが実行されて、ミリ秒単位で時間の合計|0 ～ start_time と end_time の間の違いです。 手順についてはキューに置かれた 0 を返します。|  
|row_count|**bigint**|行の合計数が変更されたか、この要求によって返される|変更またはデータ、それ以外の場合の影響を受ける行の数を返すしていないするステップの 0 を返します。 DMS の手順に達すると-1 に設定されます。|  
|command|nvarchar (4000)|このステップのコマンドの完全なテキストを保持します。|ステップの任意の有効な要求文字列。 4,000 文字より長い場合に切り捨てられます。|  
  
## <a name="see-also"></a>参照  
 [PolyBase 動的管理ビューでのトラブルシューティング](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
