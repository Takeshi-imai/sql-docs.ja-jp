---
title: "SQL Server エージェントの Jobs オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f372eced96ca17d4fd547a11a56cfefd732394b9
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-agent-jobs-object"></a>SQL Server エージェントの Jobs オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] SQL Server エージェントの **Jobs** パフォーマンス オブジェクトには、SQL Server エージェントのジョブについての情報を報告するパフォーマンス カウンターが含まれています。 次の表は、このオブジェクトに含まれているカウンターを示します。  
  
 次の表には **SQLAgent:Jobs** カウンターが含まれています。  
  
|[オブジェクト名]|Description|  
|----------|-----------------|  
|**Active Jobs**|このカウンターは、現在実行中のジョブの数を報告します。|  
|**Failed jobs**|このカウンターは、失敗して終了したジョブの数を報告します。|  
|**Job success rate**|このカウンターは、実行済みジョブのうち問題なく完了したジョブの割合を報告します。|  
|**Jobs activated/minute**|このカウンターは、最後の 1 分間に起動されたジョブの数を報告します。|  
|**Queued jobs**|このカウンターは、SQL Server エージェントで実行する準備が整っているジョブで、まだ実行が開始されていないジョブの数を報告します。|  
|**Successful jobs**|このカウンターは、問題なく終了したジョブの数を報告します。|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|Instance|Description|  
|--------------|-----------------|  
|**_Total**|すべてのジョブの情報です。|  
|**警告**|警告によって開始されたジョブの情報です。|  
|**Others**|警告またはスケジュールによって開始されたジョブの情報です。 通常、これらのジョブは **sp_start_job**を使用して手動で開始されます。|  
|**スケジュール**|スケジュールによって開始されたジョブの情報です。|  
  
## <a name="see-also"></a>参照  
 [ジョブの実装](http://msdn.microsoft.com/library/69e06724-25c7-4fb3-8a5b-3d4596f21756)   
 [パフォーマンス オブジェクトの使用](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
