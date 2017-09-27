---
title: "SQL Server 監査ログの表示 | Microsoft Docs"
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
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: caff5bab9e303b299a31005b1add0f0c807f6ef5
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="view-a-sql-server-audit-log"></a>SQL Server 監査ログの表示
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で SQL Server 監査ログを表示する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **SQL Server 監査ログを表示する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 **CONTROL SERVER** 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-a-sql-server-audit-log"></a>SQL Server 監査ログを表示するには  
  
1.  オブジェクト エクスプローラーで、 **[セキュリティ]** フォルダーを展開します。  
  
2.  **[監査]** フォルダーを展開します。  
  
3.  表示する監査ログを右クリックし、 **[監査ログの表示]**をクリックします。 **server_name**** ダイアログ ボックスが開きます。 詳細については、「 [Log File Viewer F1 Help](../../../relational-databases/logs/log-file-viewer-f1-help.md)」を参照してください。  
  
4.  完了したら、 **[閉じる]**をクリックします。  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] では、[ログ ファイルの表示] を使用して監査ログを表示することをお勧めします。 ただし、自動監視システムを作成している場合、[sys.fn_get_audit_file &#40;Transact-SQL&#41;](../../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md) 関数を使用して監査ファイルの情報を直接読み取ることができます。 ファイルを直接読み取ると、わずかに異なる (処理されていない) 形式でデータが返されます。 詳細については、 **sys.fn_get_audit_file** に関するページを参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server Audit &#40;データベース エンジン&#41;](../../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [セキュリティ ログへの SQL サーバー監査イベントの書き込み](../../../relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log.md)  
  
  