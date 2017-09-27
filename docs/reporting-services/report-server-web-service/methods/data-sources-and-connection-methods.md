---
title: "データ ソースとの接続方法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- connections [Reporting Services], data sources
- reports [Reporting Services], data
- data sources [Reporting Services], methods
ms.assetid: 50999b52-fc7c-4333-9fb0-d04c37a4c90f
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 922c7fbd680a9d82713db30d8df5f0ae5a40401a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="data-sources-and-connection-methods"></a>データ ソースと接続のメソッド
  これらのメソッドを使用して、データ ソースの接続と資格情報を設定および管理できます。  
  
|方法|操作|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataSource%2A>|レポート サーバー データベースまたは SharePoint ライブラリの新しいデータ ソースを作成します。|  
|<xref:ReportService2010.ReportingService2010.DisableDataSource%2A>|有効になっているデータ ソースを無効にします。|  
|<xref:ReportService2010.ReportingService2010.EnableDataSource%2A>|無効なデータ ソースを有効にします。|  
|<xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A>|データ ソースの内容を返します。|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSourcePrompts%2A>|指定したアイテムのデータ ソース表示名を取得します。|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSources%2A>|カタログ内のアイテムのデータ ソースを返します。|  
|<xref:ReportService2010.ReportingService2010.ListDependentItems%2A>|指定したカタログ アイテムを参照するカタログ アイテムの一覧を返します。|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptionsUsingDataSource%2A>|指定したデータ ソースに関連付けられたサブスクリプションの一覧を返します。|  
|<xref:ReportService2010.ReportingService2010.SetDataSourceContents%2A>|データ ソースに関連付けられた接続プロパティを設定します。|  
|<xref:ReportService2010.ReportingService2010.SetItemDataSources%2A>|レポート サーバー データベースまたは SharePoint ライブラリのアイテムのデータ ソースを設定します。|  
|<xref:ReportService2010.ReportingService2010.TestConnectForDataSourceDefinition%2A>|データ ソースへの接続をテストします。 このメソッドは、データ ソースのテストを直接実行できます。|  
|<xref:ReportService2010.ReportingService2010.TestConnectForItemDataSource%2A>|データ ソースへの接続をテストします。 このメソッドは、レポートまたはモデルで使用されるパブリッシュされたデータ ソースと、共有データ ソースのテストをサポートします。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [レポート サーバー Web サービス メソッド](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  