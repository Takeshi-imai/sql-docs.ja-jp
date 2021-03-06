---
title: "SQL Server XTP IO ガバナー | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
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
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
caps.latest.revision: 
author: dagiro
ms.author: v-dagir
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d6a4ca0d1fc0bf90deffa47e71547b966e25f4b5
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-xtp-io-governor"></a>SQL Server XTP IO ガバナー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server XTP IO ガバナーのパフォーマンス オブジェクトには、インメモリ OLTP IO レート ガバナーに関連するカウンターが含まれています。

次の表で、 **SQL Server XTP IO ガバナー** カウンターについて説明します。

|カウンター|Description|  
|-------------|-----------------|  
|**1 秒あたりの不十分なクレジット待機数**|レート オブジェクトのクレジット不足に起因する待機数 (1 秒あたり)。|
|**1 秒あたりに発行された Io 数**|フラッシュ スレッドにより発行された Io 数 (1 秒あたり)。|
|**1 秒あたりのログ ブロック数**|コントローラーによって処理されたログ ブロック数 (1 秒あたり)。|
|**実行されなかったクレジット スロット数**|レート オブジェクトからのクレジットを待ったために実行されなかったクレジット スロット数。|
|**1 秒あたりの古いレート オブジェクト待機数**|古いレート オブジェクトに起因する待機数 (1 秒あたり)。|
|**公開されたレート オブジェクトの合計**|公開されたレート オブジェクトの合計数。|
 

## <a name="see-also"></a>参照  
[SQL Server XTP &#40;インメモリ OLTP&#41; パフォーマンス カウンター](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)
