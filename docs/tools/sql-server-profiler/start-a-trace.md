---
title: "トレースの開始 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Profiler, stopping traces
- pausing traces
- Profiler [SQL Server Profiler], stopping traces
- Profiler [SQL Server Profiler], starting traces
- traces [SQL Server], starting
- SQL Server Profiler, pausing traces
- traces [SQL Server], stopping
- Profiler [SQL Server Profiler], pausing traces
- traces [SQL Server], pausing
- SQL Server Profiler, starting traces
- stopping traces
- starting traces
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
caps.latest.revision: "24"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ef0d4c1015fa70145f8539a4dd10f4f8f6ffc35b
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="start-a-trace"></a>トレースの開始
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]新しいトレースを定義するかを使用してテンプレートを作成した後[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]、開始、一時停止、または新しいトレース定義またはテンプレートを使用してデータのキャプチャを停止することができます。  
  
## <a name="starting-a-trace"></a>トレースの開始  
 定義されているトレース元が [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] または [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスである場合、トレースを開始すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により、キャプチャしたサーバー イベントを一時的に保持する場所を提供するキューが作成されます。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して SQL トレースにアクセスすると、トレース ウィンドウが表示されていない場合、トレースの開始時に新しいトレース ウィンドウが表示され、データがすぐにキャプチャされます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] システム ストアド プロシージャを使用して SQL トレースにアクセスする際には、データをキャプチャする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが起動されるたびにトレースを開始する必要があります。 トレースの開始後に変更できるのはトレースの名前のみです。  
  
> [!NOTE]  
>  既存のトレースを使用する場合、プロパティを参照できますが、変更できません。 プロパティを変更するには、トレースを停止または一時停止する必要があります。  
  
## <a name="see-also"></a>参照  
 [サーバー &#40; への接続後の自動的なトレースを開始します。SQL Server Profiler &#41;](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [トレース &#40; を一時停止します。SQL Server Profiler &#41;](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)   
 [トレース &#40; を停止します。SQL Server Profiler &#41;](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)   
 [トレース ウィンドウ &#40; をオフにSQL Server Profiler &#41;](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)   
 [一時停止または停止したトレースの再開 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  
