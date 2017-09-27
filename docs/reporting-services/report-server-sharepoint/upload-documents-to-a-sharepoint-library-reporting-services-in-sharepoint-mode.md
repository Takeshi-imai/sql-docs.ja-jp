---
title: "ドキュメントをアップロード SharePoint ライブラリに Reporting Services SharePoint モード |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- SharePoint integration [Reporting Services], content management
- uploading reports [Reporting Services]
ms.assetid: 93bd1b19-061b-409f-8dc2-ec416b2f4b39
caps.latest.revision: 11
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 51cf021c47749367bba6fcc08081dfeed688298f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode"></a>SharePoint ライブラリへのドキュメントのアップロード (Reporting Services の SharePoint モード)
  レポート定義やレポート モデルを SharePoint ライブラリにアップロードすることができます。 レポート サーバー アイテムをアップロードするときには、ライブラリまたはライブラリ内のフォルダーを選択する必要があります。 レポート サーバー アイテムを一覧やページにアップロードすることはできません。  
  
 データ ソース (.rds) ファイルをアップロードすることはできません。 ただし、.rds ファイルをデザイン ツール (レポート デザイナーなど) から SharePoint ライブラリにパブリッシュすることはできます。 パブリッシュ時に、ソリューション内の元の .rds ファイルから新しい .rsds ファイルが作成されます。 SharePoint ライブラリに新しい .rsds ファイルを作成して、その新しい接続が使用されるように、アップロードしたレポートやモデルのデータ ソース接続プロパティを設定することもできます。  
  
> [!NOTE]  
>  レポート サーバーは SharePoint モード用に構成しておく必要があります。また、SharePoint 製品のインスタンスに、SharePoint サイトからレポート サーバー アイテムを格納しレポート サーバー アイテムにアクセスするプログラム ファイルを提供する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインが必要です。  
  
 ドキュメントをライブラリにアップロードするには、サイト レベルの "アイテムの追加" 権限が必要です。 既定のセキュリティ設定を使用している場合、この権限は、フル コントロール レベルの権限を持つ **所有者** グループおよび投稿レベルの権限を持つ **メンバー** グループのメンバーに与えられます。  
  
### <a name="to-add-a-report-definition-or-report-model-to-a-library"></a>レポート定義またはレポート モデルをライブラリに追加するには  
  
1.  ライブラリまたはライブラリ内のフォルダーを開きます。 まだライブラリが開いていない場合は、サイド リンク バーでライブラリの名前をクリックします。 ライブラリの名前が表示されていない場合は、 **[すべてのサイト コンテンツの表示]**をクリックし、ライブラリの名前をクリックします。  
  
2.  **[アップロード]** メニューの **[ドキュメントのアップロード]**をクリックします。  
  
3.  1 つのレポート ファイルまたはレポート モデル ファイルをアップロードするには、レポート定義 (.rdl) ファイルまたはレポート モデル (.smdl) ファイルを選択し、 **[OK]**をクリックします。  
  
     レポート定義で共有データ ソース (.rsds) ファイルを使用して接続情報を外部データ ソースに格納している場合は、.rdl ファイルと .rsds ファイルを同時にアップロードできます。 これには、 **[複数のドキュメントのアップロード]**をクリックし、両方のファイルを指定して、 **[OK]**をクリックします。  
  
 共有データ ソース、レポート モデル、またはサブレポートへの参照が含まれているレポートをアップロードすると、ファイルのアップロード時にレポート内で参照が破損します。 参照のリセット方法の詳細については、「[共有データ ソースを作成および管理する &#40;Reporting Services の SharePoint 統合モード&#41;](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76)」を参照してください。  
  
 レポートをアップロードした場合は、そのレポートを開くとレポートがオンデマンドで実行されて、データ ソースからライブ データが取得されます。 スケジュールに基づいたデータ取得や、キャッシュされたデータの使用が行われるようにレポートを構成することもできます。 詳細については、「[処理オプションの設定 &#40;Reporting Services の SharePoint 統合モード&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)」を参照してください。  
  
 レポートにパラメーターを含めると、ユーザーがデータをフィルター選択できるようになります。 パラメーターは、特定の値を使用するように構成したり、表示方法を変更したりすることができます。 詳細については、「[パブリッシュ済みレポートのパラメーターを設定する方法 &#40;Reporting Services の SharePoint 統合モード&#41;](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SharePoint ライブラリにレポートをパブリッシュします。](../../reporting-services/reports/publish-a-report-to-a-sharepoint-library.md)   
 [SharePoint ライブラリに共有データ ソースをパブリッシュします。](../../reporting-services/reports/publish-a-shared-data-source-to-a-sharepoint-library.md)   
 [SharePoint サイト上のレポート サーバー アイテムに対する権限の許可](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  