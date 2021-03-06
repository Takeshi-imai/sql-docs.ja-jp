---
title: "定期データ更新とデータ ソースに Windows 認証は行われません |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8d875bc-7823-46b7-a939-867cefd4de12
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9dadc46f53cff296a0332069165a9faa876e6180
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="schedule-data-refresh-and-data-sources---no-windows-authentication"></a>定期データ更新とデータ ソースに Windows 認証は行われません
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
このトピックでは、Windows 認証をサポートしない [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**データ ソースを使用できる** for SharePoint 定期データ更新のワークフローについて説明します。 たとえば、Oracle データ ソースまたは IDM DB2 データ ソースが該当します。 このトピックにある図と手順では、Oracle データ ソースを参照していますが、他のデータ ソースにも同じワークフローが当てはまります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010 &#124; SharePoint 2013|  
  
 **概要:** 2 つの Secure Store ターゲット アプリケーションを作成します。 1 つ目のターゲット アプリケーション (PowerPivotDataRefresh) を、Windows 資格情報を使用するように構成します。 2 つ目のターゲット アプリケーションを、Windows 認証をサポートしていないデータ ソース (Oracle データベースなど) の資格情報を使用して構成します。 さらに、2 つ目のターゲット アプリケーションでは、自動データ更新アカウントに 1 つ目のターゲット アプリケーションを使用します。  
  
 ![as_powerpivot_refresh_no_windows_auth](../../analysis-services/power-pivot-sharepoint/media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")  
  
-   **(1) PowerPivotDatarefresh:** Windows 認証で設定される Secure Store ターゲット アプリケーション ID。  
  
-   **(2) OracleAuthentication:** Oracle 資格情報で設定される Secure Store ターゲット アプリケーション ID。  
  
-   **(3)** [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションは、自動データ更新アカウントにターゲット アプリケーション **PowerPivotDataRefresh**を使用するよう構成されます。  
  
-   **(4)** PowerPivot ブックでは Oracle データが使用されます。 ブックの更新設定では、データ ソースへの接続で、資格情報にターゲット アプリケーション **(2)** を使用するよう指定します。  
  
## <a name="prerequisites"></a>前提条件  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションがある。  
  
-   Secure Store Service アプリケーションがある。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ モデルを含む Excel ブックがある。  
  
## <a name="to-create-a-target-application-id-that-uses-windows-authentication"></a>Windows 認証を使用するターゲット アプリケーション ID を作成するには  
  
1.  SharePoint サーバーの全体管理で **[サービス アプリケーションの管理]**をクリックします。  
  
2.  Secure Store Service アプリケーションの名前をクリックします。  
  
3.  **[管理]** ページで **[新規作成]**をクリックします。 ![as_powerpivot_refresh_sss_new_target_application](../../analysis-services/power-pivot-sharepoint/media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")  
  
4.  **[Secure Store のターゲット アプリケーションを新規に作成します]** ページで、次の値を構成します。  
  
    -   **ターゲット アプリケーション ID:** PowerPivotDataRefresh  
  
    -   **表示名:** PowerPivotDataRefresh  
  
    -   **連絡先の電子メール:** ?  
  
    -   **ターゲット アプリケーションの種類:** グループ  
  
    -   **ターゲット アプリケーション ページの URL:** なし  
  
5.  **[次へ]**をクリックします。  
  
6.  [資格情報] ページで、 **[Windows ユーザー名]** と **[Windows パスワード]**の 2 つのフィールド名とフィールドの種類は既定値のままにします。  
  
7.  **[次へ]**をクリックします。  
  
8.  **[メンバーシップの設定]** ページで、 **[ターゲット アプリケーションの管理者]** に 1 人以上を追加し、ターゲット アプリケーションへのアクセスが必要なメンバーを追加します。  
  
9. **[OK]**をクリックします。  
  
10. 新しいターゲット アプリケーション ID が一覧に追加されます。 ターゲット アプリケーション ID を選択し、クリックして**資格情報の設定**![as_powerpivot_refresh_sss_set_key](../../analysis-services/power-pivot-sharepoint/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")です。  
  
11. Windows ユーザー名と Windows パスワードを入力して、 **[OK]**をクリックします。  
  
## <a name="to-create-a-target-application-id-that-uses-oracle-credentials"></a>Oracle 資格情報を使用するターゲット アプリケーション ID を作成するには  
  
1.  SharePoint サーバーの全体管理で **[サービス アプリケーションの管理]**をクリックします。  
  
2.  Secure Store Service アプリケーションの名前をクリックします。  
  
3.  **管理**] ページで [**新規**![as_powerpivot_refresh_sss_new_target_application](../../analysis-services/power-pivot-sharepoint/media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application").  
  
4.  **[Secure Store のターゲット アプリケーションを新規に作成します]** ページで、次の値を構成します。  
  
    -   **ターゲット アプリケーション ID:** OracleAuthentication  
  
    -   **表示名:** OracleAuthentication  
  
    -   **連絡先の電子メール:** ?  
  
    -   **ターゲット アプリケーションの種類:** グループ  
  
    -   **ターゲット アプリケーション ページの URL:** なし  
  
5.  **[次へ]**をクリックします。  
  
6.  **[資格情報]** ページで、最初のフィールド名を **Oracle User ID** に変更し、 **フィールドの種類** を **User Name**に変更します。  
  
     2 つ目のフィールド名を **Oracle Password** に変更し、 **フィールドの種類** を **Password**に変更します。  
  
7.  **[次へ]**をクリックします。  
  
8.  **[メンバーシップの設定]** ページで、 **[ターゲット アプリケーションの管理者]** に 1 人以上を追加し、ターゲット アプリケーションへのアクセスが必要なメンバーを追加します。  
  
9. **[OK]**をクリックします。  
  
10. 新しいターゲット アプリケーション ID が一覧に追加されます。 ターゲット アプリケーション ID を選択し、クリックして**資格情報の設定**![as_powerpivot_refresh_sss_set_key](../../analysis-services/power-pivot-sharepoint/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")です。  
  
11. Oracle ユーザー ID と Oracle パスワードを入力して、 **[OK]**をクリックします。  
  
 詳細については、「 [SQL Server 認証で Secure Store を使用する (SharePoint Server 2013)](http://technet.microsoft.com/library/gg298949.aspx) 」(http://technet.microsoft.com/library/gg298949.aspx) の「SQL Server 認証用にターゲット アプリケーションを作成するには」をご覧ください。  
  
## <a name="to-configure-the-power-pivot-service-application"></a>Power Pivot サービス アプリケーションを構成するには  
  
1.  SharePoint サーバーの全体管理で [サービス アプリケーションの管理] をクリックします。  
  
2.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションの名前 (たとえば "Default [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Service Application") をクリックします。  
  
3.  [アクション] で **[サービス アプリケーションの設定の構成]** をクリックします。  
  
4.  **[データ更新]** の **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 自動データ更新アカウント**を**[PowerPivotDataRefresh]** に設定し、 **[OK]**をクリックします。  
  
     ![as_powerpivot_refresh_new_refresh_acount](../../analysis-services/power-pivot-sharepoint/media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")  
  
## <a name="to-configure-the-workbook"></a>ブックを構成するには  
  
1.  ブックを参照、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]ギャラリーとクリック**データ更新の管理**![as_powerpivot_refresh_manage_reresh](../../analysis-services/power-pivot-sharepoint/media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh").  
  
2.  **[データ更新の履歴]** ページが表示されたら、 **[スケジュールの構成]**をクリックします。  
  
3.  **[有効化]**をクリックします。  
  
4.  **[さらに、できるだけ早く更新を行います]**をクリックします。  
  
5.  **[資格情報]** で、 **[管理者によって構成されたデータ更新アカウントを使用します]**をクリックします。  
  
6.  **[すべてのデータ ソース]**をクリアします。  
  
7.  Oracle データを使用するデータ ソースに対して **[最新の情報に更新]** を選択します。 データ ソース名は、Microsoft Excel で、 **[データ]**タブの **[接続]**で **[プロパティ]** をクリックすると変更できます。  
  
8.  お使いのデータベース ソースで **[既定のスケジュールを使用する]**を選択します。  
  
9. **[Secure Store Service (SSS) に保存された資格情報を使用してデータ ソースにログオンします。資格情報を参照するための ID を SSS ID ボックスに入力してください]** を選択します。  
  
10. **[ID]** ボックスに「 **OracleAuthentication**」と入力します。  
  
11. **[OK]**をクリックします。  
  
     " `The provided Secure Store target application is either incorrectly configured or does not exist`" のようなエラー メッセージが表示される場合があります。  
  
     一般的な解決方法として、次の 2 つが挙げられます。  
  
    -   ターゲット アプリケーション ID が正しいことを確認する。  
  
    -   ターゲット アプリケーションの資格情報を設定したことを確認する。  
  
## <a name="to-verify-data-refresh-with-the-new-authentication"></a>新しい認証を使用したデータ更新を確認するには  
 **[OK]**をクリックすると、 **[更新の履歴]** ページが表示されます。 前の手順で **[さらに、できるだけ早く更新を行います]**を選択したため、数分以内に、新しい項目が更新の履歴に表示されます。 タイマー ジョブ " **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ更新タイマー ジョブ** " の既定値は 1 分です。 履歴の更新に新しい項目が表示されない場合は、しばらく待ってから、ブラウザーを更新してください。 それでも新しい項目が表示されない場合は、タイマー ジョブの現在の値を確認してください。  
  
## <a name="more-information"></a>その他の情報  
  
-   [SharePoint 2013 で Secure Store Service を構成する](http://technet.microsoft.com/library/ee806866.aspx)。  
  
-   [SharePoint 2013 と SQL Server 2012 SP1 (Analysis Services) での Power Pivot データの更新に関する記事](http://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh)の「定期データ更新」セクションをご覧ください。  
  
  
