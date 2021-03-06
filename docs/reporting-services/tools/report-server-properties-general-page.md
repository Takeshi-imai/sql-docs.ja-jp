---
title: "[サーバーのプロパティ] ([全般] ページ) | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: tools
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
caps.latest.revision: "34"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 974897a7498eb9032bbe43933b9e9931f5969449
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="report-server-properties-general-page"></a>[レポート サーバーのプロパティ] ([全般] ページ)
  このページを使用すると、レポート マネージャーで使用されるタイトルの表示と変更、個人用レポートの有効化と無効化、個人用レポートのセキュリティに関するロール定義の選択、およびクライアントの印刷コントロールの有効化または無効化ができます。  
  
 **このページを開くには:**
 1) コントロール パネルの  ◆セグ : 文が分断されているため、訳の位置が入れ替わっています◇ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]
 2) レポート サーバー インスタンスに接続します。
 3) レポート サーバー名を右クリックして、 **[プロパティ]**をクリックします。  
  
 サーバー モードによって、設定できるサーバー プロパティが決まります。 SharePoint 統合モード用に構成されたレポート サーバーを管理している場合は、個人用レポートを有効にしたり、Web ポータルのタイトルを設定したりすることができません。  
  
## <a name="options"></a>および  
 **名前**  
 Web ポータルの上部に表示される名前を入力します。 既定では、この値は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]です。 指定した名前は、レポート マネージャーでのみ表示されます。  
  
 **[バージョン]**  
 このプロパティは読み取り専用です。 使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のバージョンを示します。  
  
 **のエディション**  
 このプロパティは読み取り専用です。 現在のレポート サーバー インスタンスを指定します。 レポート マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 **認証モード**  
 このプロパティは読み取り専用です。 レポート サーバー インスタンスで受け入れられる認証要求の種類を示します。 認証モードを変更するには、 **RSReportServer.config** ファイルを編集する必要があります。 詳細については、「 [レポート サーバーでの認証](../../reporting-services/security/authentication-with-the-report-server.md)」を参照してください。  
  
 **[URL]**  
 このプロパティは読み取り専用です。 レポート サーバー Web サービスへの URL を示します。 この値は [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールで指定されます。 詳細については、「[URL の構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)」をご覧ください。  
  
 **[ユーザーごとに個人用レポート フォルダーを有効にする]**  
 ユーザーが **個人用レポート** を使用できるようにします。 このオプションはネイティブ モードのレポート サーバーでのみ使用できます。  
  
 **[個人用フォルダーごとに適用するロールを選択します]**  
 個人用レポートのセキュリティに使用するロール定義を指定します。 ロール定義は、各個人用レポート フォルダーでサポートされるタスクのセットを特定します。  

  
## <a name="see-also"></a>参照  
 [レポート サーバーのプロパティを設定する (Management Studio)](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Management Studio でレポート サーバーに接続する](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [個人用レポートの有効化と無効化](../../reporting-services/report-server/enable-and-disable-my-reports.md)   
 [Management Studio のレポート サーバーの F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [個人用レポートをセキュリティで保護する](../../reporting-services/security/secure-my-reports.md)  
  
  

