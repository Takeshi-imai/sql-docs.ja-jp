---
title: "SQL Server Reporting Services レポート ビューアー Web パーツを SharePoint ページに追加する | Microsoft Docs"
ms.custom: 
ms.date: 09/26/2017
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
ms.openlocfilehash: 93137662ea40589495e692ca021c693920786185
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="add-sql-server-reporting-services-report-viewer-web-part-to-a-sharepoint-page"></a>SQL Server Reporting Services レポート ビューアー Web パーツを SharePoint ページに追加する

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

レポート ビューアー Web パーツを SharePoint ページに追加する方法で、SQL Server Reporting Services または Power BI Report Server からレポートを表示します。

![SharePoint ページのレポート ビューアー Web パーツ](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="prerequisites"></a>Prerequisites

* レポートを正常に読み込むには、Kerberos 制約付き委任に対して Claims to Windows Token Service (C2WTS) を構成する必要があります。 C2WTS の構成方法については、「[Claims to Windows Token Service (C2WTS) と Reporting Services](../install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md)」を参照してください。

* レポート ビューアー Web パーツは SharePoint ファームに展開する必要があります。 レポート ビューアー Web パーツ ソリューション プロジェクトを展開する方法については、「[Deploy the Report Viewer web part on a SharePoint site](deploy-report-viewer-web-part.md)」 (SharePoint サイトでレポート ビューアー Web パーツを展開する) を参照してください。

* Web パーツを Web ページに追加するには、サイト レベルでの "ページの追加とカスタマイズ" アクセス許可が必要です。 既定のセキュリティ設定を使用する場合、この権限はフル コントロール レベルの権限を持つ **所有者** グループのメンバーに与えられます。

## <a name="add-web-part"></a>Web パーツを追加する

1. SharePoint サイトで、左上にある**歯車**アイコンを選び、**[ページの追加]** を選びます。

    ![歯車アイコンから SharePoint サイトにページを追加します。](media/sharepoint-add-a-page.png)

2. ページに名前を付け、**[作成]** を選びます。

3. ページ デザイナー内で、リボンにある **[挿入]** タブを選びます。 **[パーツ]** セクション内で **[Web パーツ]** を選びます。

    ![Office リボンから Web パーツを挿入します。](media/sharepoint-insert-web-part.png)

4. **[カテゴリ] で** [SQL Server Reporting Services (ネイティブ モード)] を選びます。 **[パーツ]** で **[レポート ビューアー]** を選びます。 **[追加]** を選びます。

    ![レポート ビューアー Web パーツを追加します。](media/sharepoint-report-viewer-web-part.png)

    最初はエラーが表示されることがあります。 このエラーは、既定のレポート サーバー URL が *http://localhost* に設定されているが、その場所で利用できない可能性があることによります。

## <a name="configure-the-report-viewer-web-part"></a>レポート ビューアー Web パーツを構成する

特定のレポートを指すように Web パーツを構成するには、次のように操作します。

1. SharePoint ページを編集するとき、Web パーツの右上にある下方向矢印を選び、**[Web パーツの編集]** を選びます。

    ![Web パーツ ドロップダウンから Web ページを編集します。](media/sharepoint-edit-web-part.png)

2. レポートをホストするレポート サーバーの **[レポート サーバー URL]** を入力します。 *http://myrsserver/reportserver* のような URL になります。

3. Web パーツ内に表示するレポートのパスと名前を入力します。 これは */AdventureWorks Sample Reports/Company Sales* のようになります。 このレイでは、「*AdventureWorks Sample Reports*」という名前のフォルダーに「*Company Sales*」というレポートが入っています。

4. レポートにパラメーターが必要な場合、レポート サーバー URL とレポートの名前を入力した後、**[パラメーター]** セクション内で **[パラメーターの読み込み]** を選びます。

5. **[OK]** を選び、Web パーツ構成の変更を保存します。

6. Office リボン内の **[保存]** を選び、SharePoint ページの変更を保存します。

![SharePoint ページのレポート ビューアー Web パーツ](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="considerations-and-limitations"></a>注意点と制限事項

* レポート ビューアー Web パーツは、SharePoint 内の最新式ページでは使用できません。
* Power BI レポートと Report Viewer Web パーツは併用できません。
* ページに追加するレポート ビューアー Web パーツが表示されない場合、[レポート ビューアー Web パーツが展開されている](deploy-report-viewer-web-part.md)ことを確認します。

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
