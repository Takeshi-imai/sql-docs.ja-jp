---
title: "SOAP を使用した Reporting Services の統合 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: application-integration
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
caps.latest.revision: "45"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 9f03dea64471d7f88f39db8cd31d7eb47c4ab9ed
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="integrating-reporting-services-using-soap"></a>SOAP を使用した Reporting Services の統合
  [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API には、カスタム レポート ソリューション開発用の複数の Web サービス エンドポイントが用意されています。 現在、このエンドポイントは、管理と実行という 2 つのカテゴリに分類されます。 管理機能は、<xref:ReportService2005> エンドポイント、<xref:ReportService2006> エンドポイント、および <xref:ReportService2010> エンドポイントを介して公開されます。 <xref:ReportService2005> エンドポイントは、ネイティブ モードで構成されたレポート サーバーを管理するために使用され、<xref:ReportService2006> エンドポイントは、SharePoint 統合モード用に構成されたレポート サーバーを管理するために使用されます。 <xref:ReportService2010> は、<xref:ReportService2005> と <xref:ReportService2006> の機能をまとめたものであり、ネイティブ モード用または SharePoint 統合モード用に構成されているレポート サーバーを管理できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] では、<xref:ReportService2005> エンドポイントと <xref:ReportService2006> エンドポイントは非推奨です。 <xref:ReportService2010> エンドポイントには、両方のエンドポイントの機能と追加の管理機能が含まれています。  
  
 実行機能は <xref:ReportExecution2005> エンドポイントを介して公開され、レポート サーバーがネイティブ モードまたは SharePoint 統合モードで構成されているときに使用されます。 次の各トピックでは、これらのエンドポイントを使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows、SharePoint、および Web アプリケーションでどのようにレポート ソリューションを開発するかについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows アプリケーションでの SOAP API の使用](../../reporting-services/application-integration/integrating-reporting-services-using-soap-windows-application.md)  
 SOAP API を使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を Windows 環境に統合する方法について説明します。  
  
 [Web アプリケーションでの SOAP API の使用](../../reporting-services/application-integration/integrating-reporting-services-using-soap-web-application.md)  
 SOAP API を使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を Web 環境に統合する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [アプリケーションへの Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [レポート サーバー Web サービス](../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
