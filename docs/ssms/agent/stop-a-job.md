---
title: "ジョブの停止 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 91ff9f963367615289a5ca07b67f4e44a4db5817
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="stop-a-job"></a>Stop a Job
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのジョブを停止する方法について説明します。 ジョブとは、SQL Server エージェントで実行される特定の一連の処理のことです。  
  
-   **作業を開始する準備:**   
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **ジョブを停止する方法:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server 管理オブジェクト](#SMO)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   ジョブで **CmdExec** または **PowerShell**型のステップが現在実行されている場合、実行中のプロセス (MyProgram.exe など) は途中で強制終了されます。 途中で強制終了した場合、そのプロセスによって使用されていたファイルが開いたままになるなど、予期しない結果が発生する可能性があります。  
  
-   マルチサーバー ジョブの場合、STOP 命令はそのジョブのすべての対象サーバーに通知されます。  
  
### <a name="Security"></a>Security  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
  
#### <a name="to-stop-a-job"></a>ジョブを停止するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**、 **[ジョブ]**の順に展開し、停止するジョブを右クリックして、 **[ジョブの停止]**をクリックします。  
  
3.  複数のジョブを停止するには、 **[ジョブの利用状況モニター]**を右クリックし、 **[ジョブの利用状況の表示]**をクリックします。 [ジョブの利用状況モニター] で、停止する複数のジョブを選択してから右クリックし、 **[ジョブの停止]**をクリックします。  
  
## <a name="TSQL"></a>Transact-SQL の使用  
  
#### <a name="to-stop-a-job"></a>ジョブを停止するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
詳しくは、「 [sp_stop_job (Transact-SQL)](http://msdn.microsoft.com/en-us/64b4cc75-99a0-421e-b418-94e37595bbb0)」をご覧ください。  
  
## <a name="SMO"></a>SQL Server 管理オブジェクトの使用  
**ジョブを停止するには**  
  
Visual Basic、Visual C#、PowerShell などのプログラミング言語で **Job** クラスの **Stop** メソッドを呼び出します。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](http://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
  
