---
title: "Reporting Services での承認 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: authorization [Reporting Services]
ms.assetid: 15fc1c7b-560c-4737-b126-e0d428a1b530
caps.latest.revision: "20"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1202e4df00651505d7177ec960c2c35b70266ec9
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="authorization-in-reporting-services"></a>Reporting Services での承認
  承認は、レポート サーバー データベースの特定のリソースに対して要求された種類のアクセスに、ID を付与するかどうかを判断する処理です。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] では、ロールベースの承認アーキテクチャを使用します。つまり、そのアプリケーションでユーザーに割り当てられているロールに基づいて、各リソースにユーザー アクセス権を付与します。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のセキュリティ拡張機能には、レポート サーバーでユーザーが認証された後、そのユーザーにアクセス権を付与するための承認コンポーネントが実装されています。 SOAP API および URL アクセスを使用して、ユーザーがシステムまたはレポート サーバー アイテムに対して操作を実行しようとすると、承認が呼び出されます。 これは、セキュリティ拡張機能インターフェイス **IAuthorizationExtension2** を使用して実現されます。 前に説明したように、すべての拡張機能は、配置した拡張機能の基本インターフェイスである **IExtension** から継承されます。 **IExtension** と **IAuthorizationExtension2** は、**Microsoft.ReportingServices.Interfaces** 名前空間のメンバーです。  
  
## <a name="checking-access"></a>アクセスのチェック  
 承認でカスタム セキュリティの実装に不可欠なのはアクセス チェックです。これは、<xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> メソッドに実装されています。 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> は、ユーザーがレポート サーバーに対する操作を試行するたびに呼び出されます。 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> メソッドは、操作の種類ごとにオーバーロードされます。 フォルダー操作の場合、アクセス チェックの例は次のようになります。  
  
```  
// Overload for Folder operations  
public bool CheckAccess(  
   string userName,   
   IntPtr userToken,   
   byte[] secDesc,   
   FolderOperation requiredOperation)  
{  
   // If the user is the administrator, allow unrestricted access.  
   if (userName == m_adminUserName)   
      return true;  
  
   AceCollection acl = DeserializeAcl(secDesc);  
   foreach(AceStruct ace in acl)  
   {  
         if (userName == ace.PrincipalName)  
         {  
            foreach(FolderOperation aclOperation in   
               ace.FolderOperations)  
            {  
               if (aclOperation == requiredOperation)  
                     return true;  
            }  
         }  
   }  
   return false;  
}  
```  
  
 レポート サーバーが <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> メソッドを呼び出すときに、ログオンしているユーザーの名前、ユーザー トークン、アイテムのセキュリティ記述子、および要求された操作を渡します。 ユーザー名のセキュリティ記述子をチェックし、要求を実行する適切なアクセス許可を持っているか確認します。次に、アクセスが許可されたことを通知するには **true** を、アクセスが拒否されたことを通知するには **false** を返します。  
  
## <a name="security-descriptors"></a>セキュリティ記述子  
 レポート サーバー データベースのアイテムに対して承認ポリシーを設定する場合は、レポート マネージャーなどのクライアント アプリケーションがユーザー情報をアイテムのセキュリティ ポリシーと一緒にセキュリティ拡張機能に送信します。 このセキュリティ ポリシーとユーザー情報をまとめてセキュリティ記述子と呼びます。 セキュリティ記述子には、レポート サーバー データベースのアイテムに関する次の情報が含まれます。  
  
-   アイテムで操作を実行する権限を持っているグループまたはユーザー  
  
-   項目の種類。  
  
-   アイテムへのアクセスを制御する任意のアクセス制御リスト  
  
 セキュリティ記述子は、Web サービス <xref:ReportService2010.ReportingService2010.SetPolicies%2A> メソッドおよび <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> メソッドを使用して作成されます。  
  
### <a name="authorization-flow"></a>承認フロー  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の承認は、サーバーで動作するように構成されているセキュリティ拡張機能によって制御されます。 承認はロールベースであり、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] セキュリティ アーキテクチャによって指定された権限と操作に限定されます。 次の図は、レポート サーバー データベースのアイテムを操作するユーザーを承認するプロセスを示しています。  
  
 ![Reporting Services のセキュリティ認証フロー](../../../reporting-services/extensions/security-extension/media/rosettasecurityextensionauthorizationflow.gif "Reporting Services のセキュリティ承認フロー")  
  
 この図のように、承認は次の順序で実行されます。  
  
1.  認証が完了すると、クライアント アプリケーションは、Reporting Services Web サービスのメソッドを使用してレポート サーバーに要求を発行します。 その際、各 Web 要求の HTTP ヘッダーに認証チケットがクッキーとして追加され、レポート サーバーに渡されます。  
  
2.  アクセス チェックの前にクッキーが検証されます。  
  
3.  クッキーの有効性を確認すると、レポート サーバーは <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> を呼び出し、ユーザーに ID を割り当てます。  
  
4.  ユーザーが Reporting Services Web サービスをとおして操作を試行します。  
  
5.  レポート サーバーが <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> メソッドを呼び出します。  
  
6.  セキュリティ識別子が取得され、<xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> のカスタム セキュリティ拡張機能に渡されます。 この時点で、ユーザー、グループ、またはコンピューターがアクセス先アイテムのセキュリティ識別子と比較され、要求された操作の実行が許可されます。  
  
7.  ユーザーが承認されると、Web サービスが操作を実行し、呼び出し元アプリケーションに応答を返します。  
  
  
