---
title: "(SQL Server Profiler) ブレークポイントまで再生 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
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
- breakpoints [SQL Server]
- traces [SQL Server], replaying
ms.assetid: 3caf751e-df3b-40c7-b5e8-4490ae178e0c
caps.latest.revision: "25"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2383eb3a226beb02c7a2060af5f07b8f97011dcd
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="replay-to-a-breakpoint-sql-server-profiler"></a>ブレークポイントまでの再生 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]このトピックのトレース ファイルまたはトレースを使用して再生するテーブルにブレークポイントを設定する方法について説明[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]です。 トレースの再生を開始する前に、トレース ファイルまたはトレース テーブルにブレークポイントを設定しておくと、特定のイベントが発生したときにトレースの再生を一時停止できます。 トレース再生中にブレークポイントを使用するとデバッグが簡単になります。これは、長いトレース スクリプトの再生を短いセグメントに分けて小刻みに分析できるからです。  
  
### <a name="to-replay-to-a-breakpoint"></a>ブレークポイントまで再生するには  
  
1.  再生するトレース ファイルまたはトレース テーブルを開きます。 詳細については、「[トレース ファイルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)」を参照してください。  
  
     開いたトレース ファイルまたはトレース テーブルに、再生に必要なイベント クラスが含まれていることを確認します。 詳細については、「 [再生を実行するための必要条件](../../tools/sql-server-profiler/replay-requirements.md)」を参照してください。  
  
2.  トレース ウィンドウで、ブレークポイントとして使用するイベントをクリックします。 ブレークポイントを設定するには、次の 3 つの方法があります。  
  
    -   F9 キーを押します。  
  
    -   **[再生]** メニューの **[ブレークポイントの設定/解除]**をクリックします。  
  
    -   イベントを右クリックし、 **[ブレークポイントの設定/解除]**をクリックします。  
  
     選択したトレース イベントの横に赤い点が表示され、それがトレースのブレークポイントであることを示します。  
  
     複数のブレークポイントを設定するには、この手順を繰り返します。  
  
3.  **[再生]** メニューの **[開始]**をクリックし、トレースを再生するサーバーに接続します。  
  
4.  **[構成の再生]** ダイアログ ボックスで設定を確認し、 **[OK]**をクリックします。  
  
     再生が開始され、ブレークポイントに達すると一時停止します。  
  
5.  F5 キーを押して再生を再開し、次のブレークポイントに進みます。  
  
6.  手順 5. をトレースの最後まで繰り返します。  
  
## <a name="see-also"></a>参照  
 [カーソル &#40; までの再生します。SQL Server Profiler &#41;](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)   
 [トレースを再生します。](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
