---
title: "Excel での BI セマンティック モデル接続を使用するか、Reporting Services |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 486195ca-530f-49e8-b40d-0f817db159ee
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8fc3d2ae19c9b8237593d1b4e1b559f22c5da1ed
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="use-a-bi-semantic-model-connection-in-excel-or-reporting-services"></a>Excel または Reporting Services での BI セマンティック モデル接続の使用
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
このトピックでは、他のトピックの手順に従って作成した BI セマンティック モデル接続の使用方法について説明します。 BI セマンティック モデルを作成したことがない場合、「 [Power Pivot ブックへの BI セマンティック モデル接続の作成](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md) 」と「 [テーブル モデル データベースへの BI セマンティック モデル接続の作成](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)」を参照してください。  
  
##  <a name="bkmk_connect"></a> Excel からの接続  
 BI セマンティック モデル接続は、Analysis Services テーブル モデル データを使用する Excel などのビジネス アプリケーションでデータ ソースとして指定できます。 ここでは、Excel を使用して BI セマンティック モデル データに接続する 2 つの方法を説明します。  
  
 Excel からの BI セマンティック モデル接続には、Excel 2010 と MSOLAP.5 OLE DB プロバイダーがワークステーションにインストールされていることが必要です。 接続要件のその他の情報についてはこのセクションでさらに説明します。  
  
 **SharePoint からの起動**  
  
-   ライブラリ内の BI セマンティック モデル接続を右クリックし、 **[Excel の起動]**をクリックします。  
  
 ![スクリーン ショットの BISM サイド リンク バー コマンド](../../analysis-services/power-pivot-sharepoint/media/ssas-bism-quicklaunch.gif "スクリーン ショットの BISM サイド リンク バー コマンド")  
  
 データ接続を有効にするようにメッセージが表示されたら、 **[有効]** をクリックします。 Excel によってブックが開かれ、基になるデータ ソースのフィールドに値が入力されたピボットテーブル フィールド リストが表示されます。  
  
 **Excel からの起動**  
  
1.  Excel を起動し、ブックを開きます。 [データ] タブの [外部データの取り込み] で、 **[その他のデータ ソース]**をクリックします。  
  
2.  **[Analysis Services から]** をクリックし、データ接続ウィザードを使用して、データをインポートします。  
  
3.  BI セマンティック モデル接続ファイルの SharePoint URL ( `http://mysharepoint/shared documents/myData.bism`など) を入力します。 既定のログオン資格情報オプション **[Windows 認証を使用する]**を受け入れます。 **[次へ]**をクリックします。  
  
4.  次のページで **[次へ]** を再度クリックします。 データベースを選択するように求められますが、使用できるのは BI セマンティック モデル接続で指定されている 1 つのデータベースのみです。  
  
5.  最後のページで、表示名と説明を入力できます。 **[完了]**をクリックし、[データのインポート] ダイアログ ボックスで **[OK]** をクリックして、データをインポートします。  
  
 接続を成功させるには、クライアント コンピューターに Excel 2010 および MSOLAP.5.dll をインストールする必要があります。 このリリースの最新バージョンの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel をインストールするとプロバイダーを取得できます。または、 [Feature Pack ダウンロード ページ](http://go.microsoft.com/fwlink/?linkid=214066)から Analysis Services OLE DB プロバイダーをダウンロードすることもできます。  
  
 MSOLAP.5.dll が現在のバージョンであることを確認するには、レジストリの **HKEY_CLASSES_ROOT\MSOLAP** をチェックします。 **CurVer** が MSOLAP.5 に設定されている必要があります。  
  
 また、SharePoint の BI セマンティック モデル ファイルに対する読み取り権限も必要です。 読み取り権限には、ダウンロード権限が含まれます。 Excel によって、SharePoint から BI セマンティック モデル接続情報がダウンロードされ、 **HTTP Get**を介してデータベースへの直接接続が開かれます。 BI セマンティック モデル接続情報がローカルに保存された後は、接続要求が SharePoint に送信されることはありません。  
  
 Analysis Services サーバー上で実行されるテーブル モデルのデータベースに接続する場合、SharePoint 権限では不十分です。 このサーバー上のデータベースに対する読み取り権限も必要です。 この手順は、BI セマンティック モデル接続を作成したときに実行しておく必要があります。 詳細については、「 [テーブル モデル データベースへの BI セマンティック モデル接続の作成](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)」を参照してください。  
  
##  <a name="bkmk_use"></a> SharePoint での Reporting Services からの接続  
 BI セマンティック モデル接続は、ほとんどのデータ ソースと同じように使用できます。使用するには、データを使用するドキュメントまたはツールでそのファイルをデータ ソースとして指定します。 BI セマンティック モデル接続は別のサーバー上の物理的なデータベースを参照しますが、接続ファイルをデータ ソースのように使用します。 BI セマンティック モデル接続の SharePoint URL は、BI セマンティック モデル データを使用する [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポートの有効なデータ ソースの場所です。  
  
 SharePoint でカスタム レポートをデザインする場合、レポートを作成するユーザーには、BI セマンティック モデル接続 (.bism) ファイルおよび Business Intelligence Semantic Model データベースに対する SharePoint 権限が必要です。 接続のセキュリティ コンテキストは、レポートを作成する対話ユーザーです。  
  
  
