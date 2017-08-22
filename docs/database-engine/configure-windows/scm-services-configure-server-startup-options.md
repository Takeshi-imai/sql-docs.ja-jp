---
title: "サーバーのスタートアップ オプションの構成 (SQL Server 構成マネージャー) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters [SQL Server], startup options
- SQL Server, startup options
- single-user mode [SQL Server], starting in
- startup options [SQL Server]
- SQL Server services, setting startup options
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: afa975c31183df845300dbe3e06cc5b7ae272ae9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="scm-services---configure-server-startup-options"></a>SCM サービス - サーバー起動オプションを構成する
  このトピックでは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 構成マネージャーを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が起動するたびに使用するスタートアップ オプションを構成する方法について説明します。 スタートアップ オプションの一覧は、「 [データベース エンジン サービスのスタートアップ オプション](../../database-engine/configure-windows/database-engine-service-startup-options.md)」を参照してください。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
### <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、スタートアップ パラメーターをレジストリに書き込みます。 これらのパラメーターは、次回 [!INCLUDE[ssDE](../../includes/ssde-md.md)]を起動したときに有効になります。  
  
 クラスターでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がオンラインの間にアクティブ サーバー上で変更を行う必要があり、その変更は [!INCLUDE[ssDE](../../includes/ssde-md.md)] を再起動すると有効になります。 他のノードでは、次回のフェールオーバー時にスタートアップ オプションのレジストリが更新されます。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 サーバーのスタートアップ オプションの構成は、レジストリの関連エントリを変更できるユーザーのみが使用できます。 該当するユーザーは次のとおりです。  
  
-   ローカル管理者グループのメンバー。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって使用されるドメイン アカウント ( [!INCLUDE[ssDE](../../includes/ssde-md.md)] がドメイン アカウントで実行されるように構成されている場合)。  
  
##  <a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="to-configure-startup-options"></a>起動オプションを設定するには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]**の順にポイントして、 **[SQL Server 構成マネージャー]**をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではないため、新しいバージョンの Windows では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーはアプリケーションとして表示されません。  
    >   
    >  -   **Windows 10**:  
    >          [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを開くには、 **スタート画面**で、「SQLServerManager13.msc」( [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]の場合) と入力します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、13 をより小さい数値に置き換えます。 SQLServerManager13.msc をクリックすると、構成マネージャーが開きます。 スタート画面やタスク バーに構成マネージャーをピン留めするには、SQLServerManager13.msc を右クリックして、 **[ファイルの場所を開く]**をクリックします。 エクスプローラーでは、SQLServerManager13.msc を右クリックし、 **[スタート画面にピン留め]** または **[タスクバーにピン留め]**をクリックします。  
    > -   **Windows 8**:  
    >          [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを開くには、**検索**チャームの **[アプリ]** で、「**SQLServerManager\<バージョン>.msc**」(「**SQLServerManager13.msc**」など) と入力し、**Enter** キーを押します。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[SQL Server のサービス]**をクリックします。  
  
3.  右ペインで、**[SQL Server** *<instance_name>***]** を右クリックし、**[プロパティ]** をクリックします。  
  
4.  **[起動時のパラメーター]** タブの **[起動時のパラメーターの指定]** ボックスにパラメーターを入力し、 **[追加]**をクリックします。  
  
     たとえば、シングル ユーザー モードで起動するには、 **[起動時のパラメーターの指定]** ボックスに「 **-m** 」と入力し、 **[追加]**をクリックします。 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をシングル ユーザー モードで再起動する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを停止してください。 そうしないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって先に接続が行われ、2 番目のユーザーとして接続できなくなる場合があります。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]を再起動します。  
  
    > [!WARNING]  
    >  シングル ユーザー モードの使用後は、[起動時のパラメーター] ボックスで、 **[既存のパラメーター]** ボックスの **-m** パラメーターを選択し、 **[削除]**をクリックします。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] を再起動すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が通常のマルチユーザー モードに戻ります。  
  
## <a name="see-also"></a>参照  
 [シングル ユーザー モードでの SQL Server の起動](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)   
 [システム管理者がロックアウトされた場合の SQL Server への接続](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [SQL Server エージェント サービスの開始、停止、または一時停止](http://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)  
  
  
