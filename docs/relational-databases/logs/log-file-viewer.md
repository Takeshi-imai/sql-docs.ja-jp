---
title: "ログ ファイルの表示 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: logs
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Log File Viewer
ms.assetid: a4ea7fc8-1cb2-4c98-bc86-8991c5e748b2
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d196f3e6964f310610bf336f6311eb9f3b33a2f1
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="log-file-viewer"></a>ログ ファイルの表示
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [ログ ファイルの表示] を使用して、ログ ファイルに記録されたエラーおよびイベントに関する情報にアクセスできます。  
  
## <a name="benefits-of-using-log-file-viewer"></a>[ログ ファイルの表示] を使用する利点  
 対象となるインスタンスがオフラインの場合または開始できない場合に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカルまたはリモート インスタンスから表示できます。 登録済みサーバーから、またはプログラムにより WMI および WQL (WMI Query Language) クエリを通じて、オフラインのログ ファイルにアクセスできます。 詳細については、「 [オフライン ログ ファイルの表示](../../relational-databases/logs/view-offline-log-files.md)」を参照してください。 [ログ ファイルの表示] を使用してアクセスできるログ ファイルの種類は、次のとおりです。  
  
-   監査コレクション  
  
-   データ コレクション  
  
-   データベース メール  
  
-   ジョブ履歴  
  
-   メンテナンス プラン  
  
-   リモート メンテナンス プラン  
  
-   SQL Server  
  
-   SQL Server エージェント  
  
-   Windows NT (イベント ビューアーからアクセスできる Windows イベントもあります)  
  
## <a name="log-file-viewer-tasks"></a>[ログ ファイルの表示] のタスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|表示する情報に応じていくつかの方法で [ログ ファイルの表示] を開く方法について説明します。|[[ログ ファイルの表示] を開く](../../relational-databases/logs/open-log-file-viewer.md)|  
|登録済みサーバーを通じてオフラインのログ ファイルを表示する方法と、WMI 権限を確認する方法について説明します。|[オフライン ログ ファイルの表示](../../relational-databases/logs/view-offline-log-files.md)|  
|[ログ ファイルの表示] の F1 ヘルプを提供します。|[[ログ ファイルの表示] の F1 ヘルプ](../../relational-databases/logs/log-file-viewer-f1-help.md)|  
  
## <a name="see-also"></a>参照  
 [SQL Server Audit &#40;Database Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [SQL Server エージェント エラー ログ](http://msdn.microsoft.com/library/0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41)  
  
  
