---
title: "SetExtendedProtectionSettings メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: 
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: wmi-provider-library-reference
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
caps.latest.revision: "7"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f2c5e606cc11ad8e7026dd0d7bebe1d9395d6d2f
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="configurationsetting-method---setextendedprotectionsettings"></a>ConfigurationSetting メソッド - SetExtendedProtectionSettings
  SetExtendedProtectionSettings メソッドは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の構成ファイル (RSReportServer.config) で RSWindowsExtendedProtectionLevel プロパティと RSWindowsExtendedProtectionScenario プロパティを設定するために使用します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *ExtendedProtectionLevel*  
 RSRreportserver.config ファイルで RSWindowsExtendedProtectionLevel を設定します。 この必須の値では大文字と小文字は区別されません。  
  
 有効な値を次に示します。  
  
 `”Off | Allow | Require”`  
  
 *ExtendedProtectionScenario*  
 RSReportserver.config ファイルで RSWindowsExtendedProtectionScenario を設定します。 この必須の値では大文字と小文字は区別されません。  
  
 有効な値を次に示します。  
  
 `”Any” | “Proxy” | “Direct”`  
  
## <a name="remarks"></a>Remarks  
 RSWindowsExtendedProtectionLevel プロパティと RSWindowsExtendedProtectionScenario プロパティは、RSReportServer.config ファイルの AuthenticationTypes に RSWindowNTLM、RSWindowsNegotiate、または RSWindowsKerberos が含まれている場合に適用されます。 これらのプロパティの設定は、レポート サーバーでのユーザーとクライアント ソフトウェアの認証方法に影響します。 ExtendedProtectionLevel を **Allow** または **Require**に設定する前に、拡張保護に関するドキュメントを読むことをお勧めします。  
  
 ExtendedProtectionLevel を設定するには、ユーザーはレポート サーバーの BUILTIN\Administrators グループのメンバーである必要があります。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [RSWindowsExtendedProtectionScenario プロパティ (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionscenario-property.md)   
 [RSWindowsExtendedProtectionLevel プロパティ (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [Reporting Services での認証の拡張保護](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
