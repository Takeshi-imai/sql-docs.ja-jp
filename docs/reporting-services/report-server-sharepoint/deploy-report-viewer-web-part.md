---
title: "SQL Server Reporting Services レポート ビューアー Web パーツを SharePoint サイトに展開する | Microsoft Docs"
ms.custom: 
ms.date: 10/05/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-server-sharepoint
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f5fd405e91f9ca16caf9345a4a3e8f7852a3ad37
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="deploy-the-sql-server-reporting-services-report-viewer-web-part-on-a-sharepoint-site"></a>SQL Server Reporting Services レポート ビューアー Web パーツを SharePoint サイトに展開する

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

レポート ビューアー Web パーツは、SharePoint サイト内の SQL Server Reporting Services (ネイティブ モード) レポートを参照するために使用できるカスタム Web パーツです。 この Web パーツを使用すると、レポート サーバー上のレポートを表示、移動、印刷、およびエクスポートできます。 レポート ビューアー Web パーツは、SQL Server Reporting Services レポート サーバーまたは Power BI Report Server によって処理されるレポート定義 (.rdl) ファイルに関連付けられています。 このレポート ビューアー Web パーツは、Power BI Report Server にホストされている Power BI レポートでは使用できません。

SharePoint Server 2013 または SharePoint Server 2016 環境にレポート ビューアー Web パーツを追加するソリューション パッケージを手動で配置するには、次の手順に従います。 Web パーツを構成する場合、ソリューションを配置する手順を行う必要があります。

**レポート ビューアー Web パーツは、スタンドアロンのソリューション パッケージで、SQL Server Reporting Services の SharePoint 統合モードとは関連していません。**

## <a name="requirements"></a>必要条件

**サポートされている SharePoint Server のバージョン:**  
* SharePoint Server 2016
* SharePoint Server 2013

**サポートされている Reporting Services のバージョン:**  
* SQL Server 2008 Reporting Services (ネイティブ モード) 以降。
* Power BI レポート サーバー

## <a name="download-the-report-viewer-web-part-solution-package"></a>レポート ビューアー Web パーツのソリューション パッケージのダウンロード

レポート ビューアー Web パーツは、Microsoft ダウンロード センターから入手できます。

[レポート ビューアー Web パーツのソリューション パッケージのダウンロード](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="deploy-the-farm-solution"></a>ファーム ソリューションの配置

このセクションでは、SharePoint ファームにソリューション パッケージを展開する方法について説明します。 このタスクは一度実行するだけで済みます。

1. SharePoint サーバーの **[管理者として実行]** オプションを使用して、SharePoint 管理シェルを開きます。

2. [Add-SPSolution](https://technet.microsoft.com/library/ff607552(v=office.16).aspx) を実行し、ファーム ソリューションを追加します。

    ```
    Add-SPSolution –LiteralPath "{path to file}\ReportViewerWebPart.wsp"
    ```

    コマンドレットにより、ソリューション名、ソリューション ID、および Deployed=False が返されます。 次の手順では、ソリューションを配置します。

3. [Install-SPSolution](https://technet.microsoft.com/library/ff607534(v=office.16).aspx) コマンドレットを実行してファーム ソリューションを配置します。

    **SharePoint 2013**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -CompatibilityLevel "14,15" -GACDeployment -WebApplication {URL to web application}
    ```

    **SharePoint 2016**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -GACDeployment -WebApplication {URL to web application}
    ```

## <a name="activate-feature"></a>機能のアクティブ化

1. SharePoint サイトで、左上にある**歯車**アイコンを選び、**[サイトの設定]** を選びます。

    ![歯車アイコンを使用したサイトの設定。](media/sharepoint-site-settings.png)

    既定では、SharePoint Web アプリケーションへのアクセスにはポート 80 が使用されます。 したがって、多くの場合、「*http://<computer name>*」と入力してルート サイト コレクションを開くことで SharePoint サイトにアクセスできます。

3. **[サイト コレクションの管理]** で **[サイト コレクションの機能]** をクリックします。

4. **レポート ビューアー Web パーツ**機能が表示されるまで、ページをスクロール ダウンします。

5. **[アクティブ化]**を選びます。

    ![レポート ビューアー Web パーツ機能のアクティブ化](media/web-part-activiate-feature.png)

6. 他のサイト コレクションについても、各サイトを開き、[サイトの操作] をクリックして手順を繰り返します。

必要に応じて PowerShell を使用して、[Enable-spfeature](https://technet.microsoft.com/library/ff607803.aspx) コマンドレットを使用して、すべてのサイトでこの機能を有効にすることもできます。

```
Get-SPWebApplication "<web application url>" | Get-SPSite -Limit ALL | 
        ForEach-Object {
            Write-Host "Enabling feature for $($_.URL)"
            Enable-SPFeature -identity "ReportViewerWebPart" -URL $_.URL -ErrorAction Continue
        }
```

## <a name="remove-the-solution"></a>ソリューションの削除

SharePoint サーバーの全体管理でソリューションの取り消しを実行できますが、インストールや修正プログラムの配置に関する問題のトラブルシューティングを体系的に行う場合を除いて、**ReportViewerWebPart.wsp** ファイルを取り消す必要はありません。

1. SharePoint サーバーの全体管理で、**[システム設定]** の **[ファーム ソリューションの管理]** をクリックします。

2. **[ReportViewerWebPart.wsp]** を選択します。

3. [ソリューションの取り消し] を選択します。

### <a name="remove-the-web-part-from-site-settings"></a>Web パーツのサイトの設定からの削除

ソリューションを取り消しても、SharePoint サイト内の Web パーツ一覧からレポート ビューアー Web パーツは削除されません。 レポート ビューアー Web パーツを削除するには、次を実行します。

1. SharePoint サイトで、左上にある**歯車**アイコンを選び、**[サイトの設定]** を選びます。

    ![歯車アイコンを使用したサイトの設定。](media/sharepoint-site-settings.png)

    既定では、SharePoint Web アプリケーションへのアクセスにはポート 80 が使用されます。 したがって、多くの場合、「*http://<computer name>*」と入力してルート サイト コレクションを開くことで SharePoint サイトにアクセスできます。

2. **[Web デザイナー ギャラリー]** の **[Web パーツ]** を選択します。

3. **[ReportViewerNativeMode.dwp]** の横の**編集アイコン**を選択します。 これは、結果の最初のページには表示されない場合があります。

4. **[アイテムの削除]** を選択します。

    ![レポート ビューアー ネイティブ モード Web パーツの編集および削除](media/report-viewer-native-mode-edit-delete.png)

Web パーツの削除は、PowerShell を使用して試行できますが、これを直接実行するコマンドはありません。 スクリプトの例については、「[How to delete Web Parts from the Web Part Gallery](https://gallery.technet.microsoft.com/office/How-to-delete-Web-Parts-1132701f)」 (Web パーツ ギャラリーから Web パーツを削除する方法) を参照してください。

## <a name="supported-languages"></a>サポートされている言語

Web パーツでサポートされている言語は以下のとおりです。

* 英語 (en)
* ドイツ語 (de)
* スペイン語 (sp)
* フランス語 (fr)
* イタリア語 (it)
* 日本語 (ja)
* 韓国語 (ko)
* ポルトガル語 (pt)
* ロシア語 (ru)
* 簡体字中国語 (zh-HANS および zh-CHS)
* 繁体中国語 (zh-HANT および zh-CHT)

## <a name="next-steps"></a>次の手順

レポート ビューアー Web パーツを展開してアクティブ化したら、SharePoint ページに Web パーツを追加できます。 詳細については、「[SharePoint ページへのレポート ビューアー Web パーツの追加](add-report-viewer-web-part-to-page.md)」を参照してください。

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
