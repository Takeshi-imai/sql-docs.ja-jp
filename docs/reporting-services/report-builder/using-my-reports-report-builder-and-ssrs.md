---
title: "個人用レポート (レポート ビルダーおよび SSRS) の使用 |Microsoft ドキュメント"
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
ms.assetid: 49c3c1da-b106-41f6-9173-16ff225bade8
caps.latest.revision: 8
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 48a6c898c5381bb777863ed7569c6ac302560eb3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="using-my-reports-report-builder-and-ssrs"></a>個人用レポートの使用 (レポート ビルダーおよび SSRS)
  [個人用レポート] フォルダーは、ネイティブ モードで構成されたレポート サーバーにおいて、所有しているレポートを保存したり、操作することができる作業領域です。 他のレポート サーバー フォルダーはパブリック フォルダーであり、通常、フォルダーのコンテンツの追加や変更を行うには高度な権限が必要になります。 一方、[個人用レポート] フォルダーは、ユーザーが管理する作業領域です。 個々のユーザーが独自の設定を基にレポートやフォルダーの追加や削除を行い、リンク レポートを保存することができます。  
  
 概念的には、[個人用レポート] フォルダーは、Windows ファイル システムの [マイ ドキュメント] フォルダーに似ています。 すべてのユーザーに [個人用レポート] というフォルダーがありますが、各ユーザーがアクセスする [個人用レポート] フォルダーは、他のすべてのユーザーが使用するフォルダーとは異なる [個人用レポート] フォルダーです。 ある特定のユーザーが所有する [個人用レポート] フォルダーのコンテンツに対し、レポート サーバー管理者を除く他のユーザーがアクセスすることはできません。  
  
 個人用レポート機能は、必須機能ではなく、レポート サーバー管理者が無効にすることができます。 有効になっている場合、[ホーム] フォルダー内に [個人用レポート] フォルダーが表示されます。[個人用レポート] フォルダーには、レポート マネージャーまたは Web ブラウザーを使用してアクセスすることができます。 詳細については、次を参照してください[の検索とレポート マネージャー &#40; でレポートを表示する。レポート ビルダーおよび SSRS &#41;](/sql-docs/docs/reporting-services/report-builder/finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs).  
  
 SharePoint 統合モードで構成されたレポート サーバーには、個人用レポート フォルダーに相当するフォルダーは存在しません。 詳細については、「 [レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="ways-to-use-my-reports"></a>個人用レポートの使用方法  
 [個人用レポート] フォルダーは、ユーザーがレポートやフォルダー、その他のアイテムを追加するまでは空になっています。 [個人用レポート] フォルダーにコンテンツを追加する方法は次のとおりです。  
  
-   個人のリンク レポートを作成し、これを [個人用レポート] に保存します。 すべてのレポートから、リンク レポートを作成できるわけではありません。 詳細については、「 [リンク レポートを作成する](../../reporting-services/reports/create-a-linked-report.md)」を参照してください。  
  
-   レポート定義 (.rdl) ファイル、レポート モデル (.smdl) ファイルなどのファイルをファイル システムからアップロードします。 どんなファイルでもアップロードできますが、レポート サーバーで処理できるのは、ファイル拡張子が .rdl または .smdl のレポート ファイルのみです。 詳細についてを参照してレポート定義"で、 [Reporting Services のドキュメント](http://go.microsoft.com/fwlink/?linkid=121312)SQL Server オンライン ブックと[アップロード ファイルまたはレポートと #40 です。レポート マネージャー &#41;](../../reporting-services/reports/upload-a-file-or-report-report-manager.md).  
  
-   独自のレポートを作成し、個人用レポートにパブリッシュします。 詳細については、次を参照してください。[レポート デザイン ビュー & #40 です。レポート ビルダー"&"#41;](../../reporting-services/report-builder/report-design-view-report-builder.md).  
  
 通常、[個人用レポート] フォルダーには、ユーザー自身によるフォルダーの管理を許可する権限が設定されています。 ただし、最終的には、レポート サーバー管理者により、ユーザーが実行できる作業が決定されます。 権限が十分でないために [個人用レポート] フォルダーでの作業が行えない場合は、レポート サーバー管理者に問い合わせてください。  
  
## <a name="searching-my-reports"></a>[個人用レポート] の検索  
 レポート サーバー データベースを検索する場合、検索を行うユーザーの [個人用レポート] フォルダーのコンテンツは検索対象になりますが、他のユーザーの [個人用レポート] フォルダーのコンテンツは検索対象から除外されます。 検索結果には、アクセス権が与えられているレポートのみが表示されます。  
  
## <a name="see-also"></a>参照  
 [レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  