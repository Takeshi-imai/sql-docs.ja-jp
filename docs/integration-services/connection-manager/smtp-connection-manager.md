---
title: "SMTP 接続マネージャー | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.smtpconnection.f1
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 53e61c4ac404999314a738f0da7c5d3f5f4b4fda
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="smtp-connection-manager"></a>SMTP 接続マネージャー
  SMTP 接続マネージャーを使用すると、パッケージから簡易メール転送プロトコル (SMTP) サーバーに接続できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれるメール送信タスクでは、SMTP 接続マネージャーを使用します。  
  
 Microsoft Exchange を SMTP サーバーとして使用する場合に、Windows 認証を使用するには SMTP 接続マネージャーの構成を必要とする場合があります。 未認証の SMTP 接続を許可しないように Exchange サーバーを構成できます。  
  
## <a name="configuration-the-smtp-connection-manager"></a>SMTP 接続マネージャーの構成  
 SMTP 接続マネージャーをパッケージに追加すると、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって、実行時に SMTP 接続を解決する接続マネージャーが作成され、接続マネージャーのプロパティが設定され、接続マネージャーのパッケージの **Connections** コレクションに追加されます。 接続マネージャーの **ConnectionManagerType** プロパティは、 **SMTP**に設定されます。  
  
 SMTP 接続マネージャーは、次の方法で構成できます。  
  
-   接続文字列を指定します。  
  
-   SMTP サーバーの名前を指定します。  
  
-   使用する認証方法を指定します。  
  
    > [!IMPORTANT]  
    >  SMTP 接続マネージャーでは、匿名認証と Windows 認証のみがサポートされています。 基本認証はサポートされていません。  
  
-   電子メール メッセージを送信するときに、SSL (Secure Sockets Layer) を使用して通信を暗号化するかどうかを指定します。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [SMTP 接続マネージャー エディター](../../integration-services/connection-manager/smtp-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
## <a name="smtp-connection-manager-editor"></a>SMTP 接続マネージャー エディター
  **[SMTP 接続マネージャー エディター]** ダイアログ ボックスを使用すると、SMTP (Simple Mail Transfer Protocol) サーバーを指定できます。  
  
 SMTP 接続マネージャーの詳細については、「 [SMTP Connection Manager](../../integration-services/connection-manager/smtp-connection-manager.md)」を参照してください。  
  
### <a name="options"></a>および  
 **名前**  
 接続マネージャーの一意な名前を指定します。  
  
 **[説明]**  
 接続マネージャーの説明を記述します。 パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続マネージャーの目的について記述することをお勧めします。  
  
 **[SMTP サーバー]**  
 SMTP サーバーの名前を指定します。  
  
 **[Windows 認証を使用する]**  
 選択すると、Windows 認証を使用してサーバーへのアクセスを認証する SMTP サーバーで、メールが送信されます。  
  
> [!IMPORTANT]  
>  SMTP 接続マネージャーでは、匿名認証と Windows 認証のみがサポートされています。 基本認証はサポートされていません。  
  
> [!NOTE]  
>  SMTP サーバーとして Microsoft Exchange を使用する場合は、 **[Windows 認証を使用]** を **True**に設定する必要があります。 未認証の SMTP 接続を許可しないように Exchange サーバーを構成することもできます。  
  
 **[SSL (Secure Sockets Layer) を有効にする]**  
 選択すると、電子メール メッセージの送信時に SSL (Secure Sockets Layer) を使用して通信が暗号化されます。  
  
