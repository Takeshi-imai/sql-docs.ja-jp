---
title: "PPTX デバイス情報設定 | Microsoft Docs"
ms.custom: 
ms.date: 09/11/2015
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- render
- powerpoint
- pptx
- export
ms.assetid: 4dc2045f-8025-41a3-8f9d-5635fb24cf4a
caps.latest.revision: "6"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0b83a1cd9142dab2b74f5dbb3148576d851faf24
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="pptx-device-information-settings"></a>PPTX デバイス情報設定
  次の表は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポートを PPTX 形式で表示するデバイス情報の設定を示しています。  
  
|設定|ReplTest1|  
|-------------|-----------|  
|**[列]**|レポートに設定する列の数。 この値により、レポートの元の設定は上書きされます。|  
|**ColumnSpacing**|レポートに設定する列の間隔。 この値により、レポートの元の設定は上書きされます。|  
|**DpiX**|出力画像の水平方向の解像度。 既定値は **96**です。 **BMP**、 **GIF**、 **PNG**、 **TIFF** の各出力形式に適用されます。|  
|**DpiY**|出力画像の垂直方向の解像度。 既定値は **96**です。 **BMP**、 **GIF**、 **PNG**、 **TIFF** の各出力形式に適用されます。|  
|**EndPage**|表示するレポートの最後のページ。 既定値は **StartPage**の値です。|  
|**MarginBottom**|レポートに設定する下余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **1in**)。 この値により、レポートの元の設定は上書きされます。|  
|**MarginLeft**|レポートに設定する左余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **1in**)。 この値により、レポートの元の設定は上書きされます。|  
|**MarginRight**|レポートに設定する右余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **1in**)。 この値により、レポートの元の設定は上書きされます。|  
|**MarginTop**|レポートに設定する上余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **1in**)。 この値により、レポートの元の設定は上書きされます。|  
|**PageHeight**|レポートに設定するページの高さ (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **11in**)。 この値により、レポートの元の設定は上書きされます。|  
|**PageWidth**|レポートに設定するページの幅 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **8.5in**)。 この値により、レポートの元の設定は上書きされます。|  
|**StartPage**|表示するレポートの最初のページ。 値 **0** はすべてのページを表示することを示します。 既定値は **1**です。|  
|**UseReportPageSize**|UseReportPageSize =**false** の場合、既定のスライド サイズは PowerPoint の既定の 13.333 インチ x 7.5 インチ (16:9 の縦横比) になります。 UseReportPageSize = true の場合、既定のスライド サイズはレポートの定義ページ サイズになります。<br /><br /> 既定値は **false**です。<br /><br /> PageWidth と PageHeight の設定は、既定の幅と高さより優先されることに注意してください。|  
  
## <a name="see-also"></a>参照  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [表示拡張機能にデバイス情報設定を渡す](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [テクニカル リファレンス (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
