---
title: "トレース テーブル (SQL Server Profiler) を再生 |Microsoft ドキュメント"
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
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 6a0ad817-3d8d-4495-889d-c66a7ef9e8bb
caps.latest.revision: "25"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 59809ee9bb39c3056804a78b4744e4f832881646
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="replay-a-trace-table-sql-server-profiler"></a>トレース テーブルの再生 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]再生は、保存されているトレースを開き、もう一度再生する機能です。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] には、ユーザー接続と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証をシミュレートできるマルチスレッド再生エンジンが備わっています。 再生は、アプリケーションまたはプロセスに関する問題のトラブルシューティングを行う際に役立ちます。 問題を特定して修正を実装したら、修正されたアプリケーションまたはプロセスに対して、発生する可能性のある問題を検出したトレースを実行します。 その後、元のトレースを再生し、結果を比較します。  
  
 再生を有効にするには、監視する他のイベント クラスに加えて、特定のイベント クラスをキャプチャする必要があります。 **TSQL_Replay** トレース テンプレートを使用すると、これらのイベントが既定でキャプチャされます。 詳細については、「 [再生を実行するための必要条件](../../tools/sql-server-profiler/replay-requirements.md)」を参照してください。  
  
### <a name="to-replay-a-trace-table"></a>トレース テーブルを再生するには  
  
1.  再生に必要なイベント クラスが含まれたトレース テーブルを開きます。  
  
2.  **[再生]** メニューの **[開始]**をクリックし、トレースを再生するサーバー インスタンスに接続します。  
  
3.  **[構成の再生]** ダイアログ ボックスの **[再生オプションの基本設定]** タブで、 **[再生サーバー]**を指定します。 **[再生サーバー]** ボックスに表示されているサーバーを変更するには、 **[変更]** をクリックします。  
  
4.  必要に応じて、再生の保存先として次のいずれかを選択します。  
  
    -   **[ファイルに保存]** : 再生の保存先となるファイルを指定します。  
  
    -   **[テーブルに保存]**: 再生の保存先となるデータベース テーブルを指定します。  
  
5.  **[トレースされた順番にイベントを再生します。このオプションはデバッグを有効にします。]**または **[複数のスレッドを使用してイベントを再生します。このオプションはパフォーマンスを最適にし、デバッグを無効にします。]**のいずれかを選択します。 次の表では、これらの設定の違いについて説明します。  
  
    |オプション|説明|  
    |------------|-----------------|  
    |**[トレースされた順番にイベントを再生します。このオプションはデバッグを有効にします。]**|記録された順番にイベントを再生します。 このオプションにより、デバッグが有効になります。|  
    |**[複数のスレッドを使用してイベントを再生します。このオプションはパフォーマンスを最適にし、デバッグを無効にします。]**|このオプションでは、複数のスレッドを使用して、順序に関係なく各イベントを再生します。 このオプションにより、パフォーマンスが最適化されます。|  
  
6.  **[再生結果を表示する]** チェック ボックスをオンにすると、実行時に再生が表示されます。  
  
7.  必要に応じて、 **[再生オプションの詳細設定]**タブをクリックし、次のオプションを指定します。  
  
    -   すべてのサーバー プロセス ID (SPID) を再生するには、 **[システム SPID を再生する]**チェック ボックスをオンにします。  
  
    -   特定の SPID に属しているプロセスに再生を制限するには、 **[1 つの SPID のみ再生する]**チェック ボックスをオンにします。 **[再生する SPID]**ボックスには、SPID を入力します。  
  
    -   特定の期間に発生したイベントを再生するには、 **[日時により再生を制限する]**チェック ボックスをオンにします。 **[開始時刻]**と **[終了時刻]**の日時を選択し、再生に含める期間を指定します。  
  
    -   再生中の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によるプロセスの管理方法を制御するには、 **[ヘルス モニター オプション]**を構成します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler の実行に必要な権限](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)   
 [トレースを再生します。](../../tools/sql-server-profiler/replay-traces.md)   
 [トレース テーブル &#40; を開くSQL Server Profiler &#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
