---
title: "ジョブの有効化または無効化 | Microsoft Docs"
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
- stopping jobs
- disabling jobs
- SQL Server Agent jobs, disabling
- jobs [SQL Server Agent], disabling
ms.assetid: 5041261f-0c32-4d4a-8bee-59a6c16200dd
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c64c8738cb16a7349b6cdb2f6f1b9d95705ee7eb
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="disable-or-enable-a-job"></a>Disable or Enable a Job
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] または [!INCLUDE[tsql](../../includes/tsql_md.md)] を使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ジョブを無効にする方法について説明します。 ジョブを無効にしても、ジョブは削除されるわけではなく、必要に応じて再び有効にすることができます。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **ジョブを無効または有効にする方法:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
  
#### <a name="to-disable-or-enable-a-job"></a>ジョブを無効または有効にするには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**を展開します。  
  
3.  **[ジョブ]**を展開し、無効または有効にするジョブを右クリックします。  
  
4.  ジョブを無効にするには、 **[無効化]**をクリックします。 ジョブを有効にするには、 **[有効化]**をクリックします。  
  
## <a name="TSQL"></a>Transact-SQL の使用  
  
#### <a name="to-disable-or-enable-a-job"></a>ジョブを無効または有効にするには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- changes the name, description, and disables status of the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @new_name = N'NightlyBackups -- Disabled',  
        @description = N'Nightly backups disabled during server migration.',  
        @enabled = 0 ;  
    GO  
    ```  
  
詳細については、「 [sp_update_job (Transact-SQL)](http://msdn.microsoft.com/en-us/cbdfea38-9e42-47f3-8fc8-5978b82e2623)」を参照してください。  
  
