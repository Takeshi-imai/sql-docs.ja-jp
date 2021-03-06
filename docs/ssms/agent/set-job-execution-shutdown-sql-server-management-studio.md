---
title: "ジョブ実行のシャットダウンの設定 (SQL Server Management Studio) | Microsoft Docs"
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
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 50e6b465dc2d4e3b49239a1ed247395d5e513584
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a>Set Job Execution Shutdown (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント自体が終了する前に、実行中のジョブの終了を [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントが待機する時間を設定する方法について説明します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **SQL Server エージェント ジョブのシャットダウン時間を設定する方法:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
既定では、 **エージェント自体が終了する前に、実行中のジョブの終了を**  [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-set-job-execution-shutdown"></a>ジョブ実行のシャットダウンを設定するには  
  
1.  **オブジェクト エクスプ ローラー** で、プラス記号をクリックして、ジョブ実行のシャットダウン間隔を設定するサーバーを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[プロパティ]**を選択します。  
  
3.  **[ページの選択]**の **[ジョブ システム]**を選択します。  
  
4.  **[シャットダウン タイムアウト間隔]** (秒単位) を増やすか、または減らしてシャットダウン タイムアウト間隔を調整します。 この値により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント自体が終了される前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントが実行中のジョブの終了を待機する時間が決まります。  
  
