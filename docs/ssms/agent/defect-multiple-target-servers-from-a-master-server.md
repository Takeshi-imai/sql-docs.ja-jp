---
title: "マスター サーバーからの複数の対象サーバーの参加の解除 | Microsoft Docs"
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
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: baf80c3e31c410ba6c50eb8dbf7b9a89a0c05361
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a>Defect Multiple Target Servers from a Master Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用して、マルチサーバー管理構成から複数の対象サーバーの参加を解除する方法について説明します。 この手順はマスター サーバーから実行します。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a>マスター サーバーから複数の対象サーバーの参加を解除するには  
  
1.  **オブジェクト エクスプローラー**で、マスター サーバーとして構成するサーバーを展開します。  
  
2.  **[SQL Server エージェント]**を右クリックし、 **[マルチ サーバーの管理]**をポイントして、 **[対象サーバーの管理]**をクリックします。  
  
3.  **[命令を通知]**をクリックし、 **[命令の種類]** ボックスの一覧の **[参加解除]**をクリックします。  
  
4.  **[受信者]**で、次のいずれかの操作を行います。  
  
    -   このマスター サーバーのすべての対象サーバーの参加を解除するには、 **[すべての対象サーバー]** をクリックします。 このオプションは、現在のマルチサーバー管理構成を完全にアンインストールする場合に使用します。  
  
    -   このマスター サーバーから一部の対象サーバーだけを参加解除するには、 **[特定の対象サーバー]**をクリックし、参加を解除するサーバーの **[選択]** ボックスをクリックします。  
  
## <a name="see-also"></a>参照  
[マルチサーバー環境の作成](../../ssms/agent/create-a-multiserver-environment.md)  
[エンタープライズ全体の管理の自動化](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[Defect a Target Server from a Master Server](../../ssms/agent/defect-a-target-server-from-a-master-server.md)  
  
