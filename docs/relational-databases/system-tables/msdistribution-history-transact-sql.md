---
title: "MSdistribution_history (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- MSdistribution_history
- MSdistribution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_history system table
ms.assetid: 55665bd2-9e1d-4efc-8f60-c63a24f66b28
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa93b984ecd15cc3c0629e0eaaf6310142943dfe
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msdistributionhistory-transact-sql"></a>MSdistribution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdistribution_history**ローカル ディストリビューターに関連付けられているディストリビューション エージェントの履歴行を保持します。 このテーブルは、ディストリビューション データベースに保存されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ディストリビューション エージェントの ID。|  
|**runstatus**|**int**|実行中の状態:<br /><br /> **1** = 開始します。<br /><br /> **2** = 成功します。<br /><br /> **3** = 実行中です。<br /><br /> **4** = アイドル状態です。<br /><br /> **5** = 再試行します。<br /><br /> **6** = 失敗します。|  
|**start_time**|**datetime**|ジョブの実行開始時刻です。|  
|**time**|**datetime**|メッセージが記録された時刻です。|  
|**duration**|**int**|メッセージ セッションの実行時間 (秒) です。|  
|**コメント**|**nvarchar (4000)**|メッセージ テキストです。|  
|**xact_seqno**|**varbinary (16)**|最後に処理されたトランザクション シーケンス番号です。|  
|**current_delivery_rate**|**float**|最後の履歴エントリ以降 1 秒あたりに配信されたコマンド数の平均です。|  
|**current_delivery_latency**|**int**|最後の履歴エントリ以降で、コマンドがディストリビューション データベースに登録されてからサブスクライバーに適用されるまでの間隔です。 単位はミリ秒。|  
|**delivered_transactions**|**int**|セッション中に配信されたトランザクションの総数です。|  
|**delivered_commands**|**int**|セッションに配信されたコマンド数の合計。|  
|**average_commands**|**int**|セッション中に配信された平均コマンド数です。|  
|**delivery_rate**|**float**|1 秒あたりの平均配信コマンド数です。|  
|**delivery_latency**|**int**|コマンドがディストリビューション データベースに登録されてからサブスクライバーに適用されるまでの待機時間です。 単位はミリ秒。|  
|**total_delivered_commands**|**bigint**|サブスクリプションが作成されてから配信されたコマンドの総数です。|  
|**error_id**|**int**|内のエラーの ID、 **MSrepl_error**システム テーブル。|  
|**updateable_row**|**bit**|設定**1**履歴行を上書きできる場合です。|  
|**timestamp**|**timestamp**|このテーブルのタイムスタンプ列です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
