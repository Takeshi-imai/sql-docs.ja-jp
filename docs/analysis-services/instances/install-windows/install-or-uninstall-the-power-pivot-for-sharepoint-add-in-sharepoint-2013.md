---
title: "インストールまたは Power Pivot の SharePoint アドインのアンインストール (SharePoint 2013) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe13ce8b-9369-4126-928a-9426f9119424
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7066ed9aafe287f5ed4a2bb5ed2981d27bd0e35f
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013"></a>Power Pivot for SharePoint アドインのインストールまたはアンインストール (SharePoint 2013)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)][!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ファームでの [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] データ アクセスを提供するアプリケーション サーバー コンポーネントとバックエンド サービスのコレクションです。 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint アドイン (**spPowerpivot.msi**) は、アプリケーション サーバー コンポーネントのインストールに使用されるインストーラー パッケージです。  
  
-   このアドインは、SharePoint 2010 の配置に必須ではありません。  
  
-   このアドインは、SharePoint 2013 と SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が含まれるシングル サーバー配置では必須ではありません。 アドインによってインストールされたコンポーネントは、SharePoint モードで [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーをインストールするときに含まれます。 アドインを使用した配置例を示す図については、「 [SQL Server BI 機能の配置トポロジ](http://msdn.microsoft.com/library/39f76bc7-94e6-4dbc-bfa5-d56f4430bb26)」を参照してください。  
  
 **注** : このトピックでは、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ソリューション ファイルと [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 構成ツールのインストールについて説明します。 インストールが完了したら、構成ツールと追加機能について「[Power Pivot の構成とソリューションの配置 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)」を参照してください。  
  
 **spPowerPivot.msi**をダウンロードする方法の詳細については、「 [Microsoft® SQL Server® 2014 PowerPivot® for Microsoft SharePoint®](http://go.microsoft.com/fwlink/?LinkID=324854)」を参照してください。  
  
##  <a name="bkmk_background"></a> 背景情報  
  
-   **アプリケーション サーバー:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能には、データ ソースとしてのブックの使用、定期データ更新、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 管理ダッシュボードなどが含まれます。  
  
     [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] Analysis Services クライアント ライブラリを配置し、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] インストール ファイルをコンピューターにコピーする**Windows インストーラー パッケージ (**spPowerpivot.msi [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] ) です。 インストーラーは、SharePoint での [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能の配置や構成は行いません。 既定では、次のコンポーネントがインストールされます。  
  
    -   [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013。このコンポーネントには、PowerShell スクリプト (.ps1 ファイル)、SharePoint ソリューション パッケージ (.wsp)、および SharePoint 2013 ファームに [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] を配置するための [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 2013 構成ツールが含まれています。  
  
    -   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for Analysis Services (MSOLAP)。  
  
    -   ADOMD.NET データ プロバイダー。  
  
    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分析管理オブジェクト。  
  
-   **バックエンド サービス:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel を使用して分析データが含まれたブックを作成した場合、サーバー環境でそのデータにアクセスするには、BI サーバーが SharePoint モードで [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] を実行するように Excel Services を構成する必要があります。 SQL Server セットアップは、SharePoint Server 2013 がインストールされているコンピューターで実行することも、SharePoint ソフトウェアがインストールされていない別のコンピューターで実行することもできます。 Analysis Services には、SharePoint との依存関係はありません。  
  
     バックエンド サービスのインストール、アンインストール、構成の詳細については、次のトピックを参照してください。  
  
    -   [Power Pivot モードでの Analysis Services のインストール](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
    -   [Power Pivot for SharePoint のアンインストール](../../../sql-server/install/uninstall-power-pivot-for-sharepoint.md)  
  
##  <a name="bkmk_where_to_install"></a> spPowerPivot.msi をインストールする場所  
 ベスト プラクティスとして、構成の一貫性を確保するために、SharePoint ファームのすべてのサーバー (アプリケーション サーバーや Web フロントエンド サーバーなど) に **spPowerPivot.msi** をインストールすることをお勧めします。 インストーラー パッケージには、Analysis Services データ プロバイダーと [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] 構成ツールが含まれています。 **spPowerPivot.msi** をインストールするときに、個々のコンポーネントを除外することで、インストールをカスタマイズできます。  
  
 **データ プロバイダー:** SharePoint と SQL Server のさまざまなテクノロジで Analysis Services データ プロバイダー (Excel Services、PerformancePoint Services、Power View など) が使用されます。 **spPowerPivot.msi** をすべての SharePoint サーバーにインストールすると、Analysis Services データ プロバイダーの完全なセットと [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] の接続をファーム全体で常に使用できるようになります。  
  
> [!NOTE]  
>  Analysis Services データ プロバイダーは、 **spPowerPivot.msi**を使用して SharePoint 2013 サーバーにインストールする必要があります。 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Feature Pack に用意されている他のインストーラー パッケージには、この環境でデータ プロバイダーが必要とする SharePoint 2013 サポート ファイルが含まれていないため、これらのパッケージはサポートされていません。  
  
 **構成ツール:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 構成ツールが必須となる SharePoint サーバーは 1 台だけです。 ただし、ベスト プラクティスとして、マルチサーバー ファームでは少なくとも 2 台のサーバーに構成ツールをインストールし、一方のサーバーがオフラインの場合でも構成ツールにアクセスできるようにしておくことをお勧めします。  
  
##  <a name="bkmk_prereq"></a> 要件と前提条件  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SharePoint Server 2013。  
  
-   SharePoint 製品およびテクノロジの要件に従い、**spPowerPivot.msi** は 64 ビットのみです。  
  
-   内のサーバー[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]モード。 Excel Services では、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サーバーとして SQL Server Analysis Services インスタンスを使用します。 Analysis Services は、ローカル コンピューターでもリモート コンピューターでも実行できます。  
  
-   **権限:** [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)]をインストールするには、現在のユーザーがコンピューターの管理者であり、SharePoint ファーム管理者グループのメンバーである必要があります。  
  
-   [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] の要件と前提条件の詳細については、「 [SharePoint モードの Analysis Service サーバーのハードウェア要件とソフトウェア要件](http://msdn.microsoft.com/library/fb86ca0a-518c-4c61-ae78-7680c57fae1f)」を参照してください。  
  
##  <a name="bkmk_install"></a> Power Pivot for SharePoint をインストールするには  
 **spPowerpivot.msi** インストーラー パッケージは、グラフィカル ユーザー インターフェイスとコマンド ライン モードの両方をサポートしています。 どちらのインストール方法でも、管理者特権で .msi を実行する必要があります。 インストールが完了したら、構成ツールと追加機能について「[Power Pivot の構成とソリューションの配置 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)」をご覧ください。  
  
### <a name="user-interface-installation"></a>ユーザー インターフェイスを使用したインストール  
 グラフィカル ユーザー インターフェイスを使用して [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] をインストールするには、次の手順を実行します。  
  
1.  **SpPowerPivot.msi**を実行します。  
  
2.  ウェルカム ページで **[次へ]** をクリックします。  
  
3.  使用許諾契約書を確認して同意し、 **[次へ]**をクリックします。  
  
4.  **[機能の選択]** ページでは、すべての機能が既定で選択されています。  
  
5.  **[次へ]**をクリックします。  
  
6.  **[インストール]** をクリックしてインストールを実行し、インストールを終了します。  
  
### <a name="command-line-installation"></a>コマンド ライン インストール  
 コマンド ライン インストールでは、管理権限でコマンド プロンプトを開き、 **spPowerPivot.msi**を実行します。 例:  
  
 `Msiexec.exe /i SpPowerPivot.msi`」を参照してください。  
  
 インストール ログを作成するには、MsiExec の標準のログ スイッチを使用します。 次の例では、"v" 詳細ログ スイッチを使用して、ログ ファイル "Install_Log.txt" を作成します。  
  
```  
Msiexec.exe /i SpPowerPivot.msi /L v c:\test\Install_Log.txt  
```  
  
### <a name="quiet-command-line-installation-for-scripting"></a>スクリプト作成のためのサイレント コマンド ライン インストール  
 **/q** スイッチまたは **/quiet** スイッチを使用すると、ダイアログや警告が表示されないサイレント インストールを実行できます。 サイレント インストールは、アドインのインストールのスクリプトを作成する場合に役立ちます。  
  
> [!IMPORTANT]  
>  サイレント コマンド ライン インストールで **/q** スイッチを使用する場合、使用許諾契約書は表示されません。 インストール方法にかかわらず、このソフトウェアの使用は、使用許諾契約に基づいています。ユーザーは使用許諾契約に準拠する責任があります。  
  
 **サイレント インストールを行うには、次の手順を実行します。**  
  
1.  **管理者権限を使用して**コマンド プロンプトを開きます。  
  
2.  次のコマンドを実行します。  
  
    ```  
    Msiexec.exe /i spPowerPivot.msi /q  
    ```  
  
### <a name="command-line-installation-to-include-specific-components"></a>コマンド ラインを使用した特定のコンポーネントのインストール  
 [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] 構成ツールは、すべての SharePoint サーバーで必須というわけではありません (ただし、必要なときに使用できるように、少なくとも 2 台のサーバーにインストールすることをお勧めします)。  
  
 spPowerPivot.msi をインストールするときに、コマンド ライン オプションを使用して、 [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] 構成ツールではなく、データ プロバイダーなどの特定の項目をインストールすることができます。 構成ツール以外のすべてのコンポーネントをインストールするコマンド ラインの例を次に示します。  
  
```  
Msiexec /i spPowerPivot.msi AGREETOLICENSE="yes" ADDLOCAL=” SQL_OLAPDM,SQL_ADOMD,SQL_AMO,SQLAS_SP_Common”  
```  
  
|オプション|Description|  
|------------|-----------------|  
|Analysis_Server_SP_addin|[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成|  
|SQL_OLAPDM|MSOLAP|  
|SQL_ADOMD|ADOMD.net プロバイダー|  
|SQL_AMO|AMO プロバイダー|  
|SQLAS_SP_Common|SharePoint 2013 の Analysis Services 共通コンポーネント|  
  
##  <a name="bkmk_deploy_solution"></a> Power Pivot for SharePoint 2013 構成ツールを使用した SharePoint ソリューション ファイルのデプロイ  
 spPowerPivot.msi によって、3 つの SharePoint ソリューション ファイルがハード ドライブにコピーされます。 ソリューション ファイルのスコープは 1 つが Web アプリケーション レベル、残り 2 つがファーム レベルです。 次のファイルがあります。  
  
-   `PowerPivotFarmSolution.wsp`  
  
-   `PowerPivotFarm14Solution.wsp`  
  
-   `PowerPivotWebApplicationSolution.wsp`  
  
 ソリューション ファイルは次のフォルダーにコピーされます。  
  
 `ssInstallPathTools\PowerPivotTools\SPAddinConfiguration\Resources`  
  
 .msi をインストールした後、 [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] 構成ツールを実行して、SharePoint ファームでソリューションを構成し、配置します。  
  
 **構成ツールを起動するには、次の手順を実行します。**  
  
 Windows のスタート画面から「power」と入力し、[アプリ] の検索結果で **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 の構成**をクリックします。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のセットアップによって SharePoint 2010 と SharePoint 2013 のそれぞれの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールがインストールされるため、検索結果には 2 つのリンクが含まれる場合があります。 必ず SharePoint 2013 構成ツールの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] を起動してください。  
  
 ![2 つの PowerPivot 構成ツール](../../../analysis-services/instances/install-windows/media/as-powerpivot-configtools-bothicons.gif "2 つの PowerPivot 構成ツール")  
  
 **Or**  
  
1.  **[スタート]**ボタンをクリックし、 **[すべてのプログラム]**をポイントします。  
  
2.  [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]をクリックします。  
  
3.  **[構成ツール]**をクリックします。  
  
4.  **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 の構成**をクリックします。  
  
 構成ツールの詳細については、「 [Power Pivot Configuration Tools](../../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)」を参照してください。  
  
##  <a name="bkmk_remove_addin"></a> アドインのアンインストールまたは修復  
  
> [!CAUTION]  
>  **spPowerPivot.msi** をアンインストールすると、データ プロバイダーと構成ツールがアンインストールされます。 データ プロバイダーをアンインストールすると、サーバーは [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]に接続できなくなります。  
  
 [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] をアンインストールまたは修復するには、次のいずれかの方法を使用します。  
  
1.  **Windows コントロール パネル:** [ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]**[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013**] を選択します。 **[アンインストール]** または **[修復]**をクリックします。  
  
2.  spPowerPivot.msi を実行し、 **[削除]** または **[修復]** を選択します。  
  
 **コマンド ライン:** コマンド ラインを使用して [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 を修復またはアンインストールするには、 **管理者権限で** コマンド プロンプトを開き、次のいずれかのコマンドを実行します。  
  
-   修復するには、次のコマンドを実行します。  
  
    ```  
    msiexec.exe /f spPowerPivot.msi  
    ```  
  
 スイッチまたは  
  
-   アンインストールするには、次のコマンドを実行します。  
  
    ```  
    msiexec.exe /uninstall spPowerPivot.msi  
    ```  
  
  
