---
title: "SQL Server: Broker TO Statistics オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 54599c96e1a89b7d4e7ae102cc09efa3c0345bf9
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-broker-to-statistics-object"></a>SQL Server: Broker TO Statistics オブジェクト
  SQLServer:Broker TO Statistics パフォーマンス オブジェクトは、[!INCLUDE[ssSB](../../includes/sssb-md.md)] ダイアログが転送オブジェクトを要求した回数、および転送オブジェクトが **tempdb** に書き込まれた頻度に関する情報を報告します。  
  
 転送オブジェクトには、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ダイアログのメッセージ転送状態が記録されます。 このオブジェクトはメモリに格納されます。 メモリを解放するために、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] は非アクティブな転送オブジェクトのバッチを定期的に **tempdb**内の作業テーブルに書き込みます。  
  
 次の表は、このオブジェクトに含まれているカウンターの一覧です。  
  
|SQL Server Broker TO Statistics カウンター|Description|  
|----------------------------------------------|-----------------|  
|**平均Length of Batched Writes**|バッチに保存される転送オブジェクトの平均数。|  
|**平均Time To Write Batch (ms)**|転送オブジェクトのバッチを保存するために必要な平均時間 (ミリ秒)。|  
|**平均Time to Write Batch Base**|内部使用のみです。|
|**平均Time Between Batches (ms)**|転送オブジェクトのバッチが書き込まれる時間間隔の平均値 (ミリ秒)。|  
|**平均Time Between Batches Base**|内部使用のみです。| 
|**Tran Object Gets/sec**|ダイアログが転送オブジェクトを要求した 1 秒あたりの回数。|  
|**Tran Objects Marked Dirty/sec**|転送オブジェクトがダーティとマークされた 1 秒あたりの回数。 最初の変更でメモリ内のコピーが **tempdb**に格納されているコピーと同一でなくなると、転送オブジェクトがダーティとマークされます。 転送オブジェクトは、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] がダイアログのメッセージ転送状態の変化を記録する必要がある場合に変更されます。|  
|**Tran Object Writes/sec**|転送オブジェクトのバッチが **tempdb** の作業テーブルに書き込まれた 1 秒あたりの回数。 書き込み回数が多い場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリに負荷がかかっている可能性があります。|  
  
## <a name="see-also"></a>参照  
 [SQL Server の Access Methods オブジェクト](../../relational-databases/performance-monitor/sql-server-access-methods-object.md)   
 [SQL Server: Memory Manager オブジェクト](../../relational-databases/performance-monitor/sql-server-memory-manager-object.md)   
 [リソースの利用状況の監視 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  