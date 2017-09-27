---
title: "バックアップし、復元の Reporting Services SharePoint サービス アプリケーション |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfb4ed77-90e5-4273-b690-89a945508ed2
caps.latest.revision: 12
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a4f320a1e806dce3411137abc74f2fe07bab7217
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="backup-and-restore-reporting-services-sharepoint-service-applications"></a>Reporting Services SharePoint サービス アプリケーションのバックアップと復元
  このトピックでは、SharePoint サーバーの全体管理または PowerShell を使用して、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションをバックアップおよび復元する方法について説明します。 このトピックの内容は次のとおりです。  
  
-   [制限事項と制約事項](#bkmk_Restrictions)  
  
-   [推奨事項](#bkmk_recommendations)  
  
-   [サービス アプリケーションのバックアップ](#bkmk_backup)  
  
-   [サービス アプリケーションの復元](#bkmk_restore)  
  
##  <a name="bkmk_BeforeYouBegin"></a> はじめに  
  
###  <a name="bkmk_Restrictions"></a> 制限事項と制約事項  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サービス アプリケーションは部分的にバックアップおよび復元バックアップおよび復元機能、SharePoint を使用します。 これには**追加の手順が必要** であり、その手順はこのトピック内に記載されています。 現在、バックアップ プロセスでは、自動実行アカウント (UEA) または Windows 認証用の暗号化キーと資格情報は **データベースにバックアップ** されません [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。  
  
###  <a name="bkmk_recommendations"></a> 推奨事項  
  
-   SharePoint のバックアップを開始する前に、暗号化キーをバックアップしてください。 暗号化キーをバックアップしなかった場合は、サービス アプリケーションの復元後に、暗号化されたデータへアクセスできなくなります。 その場合、暗号化されたデータを削除する必要が生じます。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションがデータベースへのアクセス用に UEA または Windows 認証を使用しているかどうかを確認してください。 これらのいずれかを使用している場合は、復元プロセス後にサービス アプリケーションを正しく構成できるよう、適切な資格情報を確認してください。  
  
-   SharePoint のバックアップ ログが、バックアップ ファイルと同じフォルダーに作成されていることを確認してください。 このファイルは通常、 **spbackup.log**という名前になります。  
  
##  <a name="bkmk_backup"></a> サービス アプリケーションのバックアップ  
 次の手順を実行します。  
  
1.  暗号化キーをバックアップします  
  
2.  サービス アプリケーションのバックアップ  
  
3.  サービス アプリケーションがデータベースへのアクセス用に UEA または Windows 認証を使用しているかどうかを確認します。 使用している場合は、復元後にサービス アプリケーションを正しく構成できるよう、必要な資格情報をメモします。  
  
### <a name="backup-the-encryption-keys-using-central-administration"></a>サーバーの全体管理を使用して暗号化キーをバックアップする  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 暗号化キーをバックアップする方法の詳細については、「 [Reporting Services SharePoint サービス アプリケーションの管理](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)」の「暗号化キー」セクションを参照してください。  
  
###  <a name="bkmk_centraladmin"></a> SharePoint サーバーの全体管理を使用してサービス アプリケーションをバックアップする  
 サービス アプリケーションをバックアップするには、次の手順を実行します。  
  
1.  SharePoint サーバーの全体管理で、 **[バックアップおよび復元]** グループの **[バックアップの実行]** をクリックします。  
  
2.  **[共有サービス]** ノードで、 **[共有サービス アプリケーション]** を展開し、サービス アプリケーションを選択します。 種類は **[SQL Server Reporting Services サービス アプリケーション]**になります。  
  
3.  **[次へ]**をクリックします。  
  
4.  **[バックアップの場所]** にパスを入力し、 **[バックアップの開始]**をクリックします。  
  
5.  上記のプロセスを繰り返します。ただし、サービス アプリケーションを選択する代わりに、 **[共有サービス プロキシ]** ノードを展開し、サービス アプリケーション プロキシを選択します。 種類は **[SQL Server Reporting Services サービス アプリケーション プロキシ]**になります。  
  
 詳細については、 SharePoint のドキュメントの次のトピックを参照してください。  
  
 [サービス アプリケーションのバックアップ (SharePoint Foundation 2010) (SharePoint ドキュメント)](http://msdn.microsoft.com/library/ee748601.aspx)。  
  
 [サービス アプリケーションのバックアップ (SharePoint Server 2010)](http://technet.microsoft.com/library/ee428318.aspx)  
  
### <a name="verify-execution-account-and-database-authentication"></a>実行アカウントとデータベース認証の確認  
 **実行アカウント** : サービス アプリケーションが実行アカウントを使用しているかどうかを確認するには、次の手順を実行します。  
  
1.  SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  サービス アプリケーションの名前をクリックし、SharePoint リボンで **[管理]** をクリックします。  
  
3.  **[実行アカウント]**をクリックします。  
  
4.  実行アカウントが構成されている場合は、サービス アプリケーションのバックアップを復元する際に資格情報が必要になります。 必ず、正しい資格情報を確認してからバックアップおよび復元の手順に進んでください。  
  
 **データベース認証** : サービス アプリケーションがデータベース認証用に Windows 認証を使用しているかどうかを確認するには、次の手順を実行します。  
  
1.  SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  サービス アプリケーションの名前をクリックし、SharePoint リボンで **[プロパティ]** をクリックします。  
  
3.  **[Reporting Services (SSRS) サービス データベース]** セクションの内容を確認します。  
  
4.  Windows 認証が構成されている場合は、サービス アプリケーションを復元後に構成する際、資格情報が必要になります。 必ず、正しい資格情報を確認してからバックアップおよび復元の手順に進んでください。  
  
##  <a name="bkmk_restore"></a> サービス アプリケーションの復元  
 次の手順を実行します。  
  
1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを復元します。  
  
2.  暗号化キーを復元します。  
  
3.  サービス アプリケーションがデータベースへのアクセス用に実行アカウントまたは Windows 認証を使用していた場合は、資格情報を構成します。  
  
### <a name="restore-the-service-application-using-sharepoint-central-administration"></a>SharePoint サーバーの全体管理を使用してサービス アプリケーションを復元する  
  
1.  SharePoint サーバーの全体管理で、 **[バックアップおよび復元]** グループの **[バックアップからの復元を実行する]** をクリックします。  
  
2.  **[バックアップ ディレクトリの場所]** ボックスにバックアップ ファイルのパスを入力し、 **[更新]**をクリックします。  
  
3.  **[トップ コンポーネント]** ボックスの一覧からサービス アプリケーションのバックアップを選択し、 **[次へ]**をクリックします。  
  
4.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションを選択し、 **[次へ]**をクリックします。  
  
5.  **[ログイン名とパスワード]** セクションで、ログイン名のパスワードを入力します。 ログイン名ボックスには、サービス アプリケーションがバックアップ以前に使用していたログインが自動入力されます。  
  
6.  **[復元の開始]**をクリックします。  
  
7.  上記のプロセスを繰り返します。ただし、サービス アプリケーションを復元する代わりに、 **[共有サービス]** ノードを展開し、 **[共有サービス アプリケーション]** ノードを展開します。  
  
 詳細については、 SharePoint のドキュメントの次のトピックを参照してください。  
  
 [サービス アプリケーションを復元する (SharePoint Foundation 2010)](http://msdn.microsoft.com/library/ee748615.aspx)。  
  
 [サービス アプリケーションを復元する (SharePoint Server 2010)](https://technet.microsoft.com/library/ee428305.aspx)。  
  
### <a name="restore-the-encryption-keys-using-central-administration"></a>サーバーの全体管理を使用して暗号化キーを復元する  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 暗号化キーを復元する方法の詳細については、「 [Reporting Services SharePoint サービス アプリケーションの管理](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)」の「暗号化キー」セクションを参照してください。  
  
### <a name="configure-the-execution-account-and-database-authentication"></a>実行アカウントとデータベース認証の構成  
 **実行アカウント** : サービス アプリケーションが実行アカウントを使用していた場合は、次の手順を実行して実行アカウントを構成します。  
  
1.  SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  サービス アプリケーションの名前をクリックし、SharePoint リボンで **[管理]** をクリックします。  
  
3.  **[実行アカウント]**をクリックします。  
  
4.  アカウントとパスワードを入力し、 **[実行アカウントの指定]** ボックスを選択します。  
  
5.  **[OK]**をクリックします。  
  
 **データベース認証** : サービス アプリケーションがデータベース認証用に Windows 認証を使用していた場合は、次の手順を実行します。  
  
1.  SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  サービス アプリケーションの名前をクリックし、SharePoint リボンで **[プロパティ]** をクリックします。  
  
3.  **[Reporting Services (SSRS) サービス データベース]** セクションの内容を確認します。  
  
4.  **[Windows 認証]**をクリックします。  
  
5.  アカウントとパスワードを入力します。 必要に応じて、 **[Windows 資格情報として使用する]** を選択します。  
  
6.  **[OK]**をクリックします。  
  
  