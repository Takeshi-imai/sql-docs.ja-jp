---
title: "SQL Server エージェントのマスター ジョブのスケジューリングの詳細の変更 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5414451-4d8e-464b-bd9e-f2b70c6899b3
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b3b08fe5a5a2e076dab9ef2f6c00b9dac86f1a56
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="change-the-scheduling-details-for-a-sql-server-agent-master-job"></a>SQL Server エージェントのマスター ジョブのスケジューリングの詳細の変更
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql_md.md)]でジョブ定義のスケジューリングの詳細を変更する方法について説明します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **以下を使用してジョブ定義のスケジューリングの詳細を変更するには:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
**sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。 詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a>ジョブ定義のスケジューリングの詳細を変更するには  
  
1.  **オブジェクト エクスプローラー** で、スケジュールを編集するジョブを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]**を展開します。  
  
3.  プラス記号をクリックして **[ジョブ]** フォルダーを展開します。  
  
4.  スケジュールを編集するジョブを右クリックして、 **[プロパティ]**をクリックします。  
  
5.  *[ジョブのプロパティ - <ジョブ名>]* ダイアログ ボックスで、**[ページの選択]** の **[スケジュール]** を選択します。 このページで利用可能なオプションの詳細については、「[ジョブのプロパティ - [新しいジョブ] ([スケジュール] ページ)](../../ssms/agent/job-properties-new-job-schedules-page.md)」をご覧ください。  
  
6.  完了したら、 **[OK]**をクリックします。  
  
## <a name="TsqlProcedure"></a>Transact-SQL の使用  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a>ジョブ定義のスケジューリングの詳細を変更するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- changes the enabled status of the NightlyJobs schedule to 0   
    -- and sets the owner to terrid.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_schedule  
        @name = 'NightlyJobs',  
        @enabled = 0,  
        @owner_login_name = 'terrid' ;  
    GO  
    ```  
  
詳しくは、「 [sp_update_schedule (Transact-SQL)](http://msdn.microsoft.com/en-us/97b3119b-e43e-447a-bbfb-0b5499e2fefe)」をご覧ください。  
  
