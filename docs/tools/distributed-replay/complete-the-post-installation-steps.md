---
title: "インストール後の手順を完了 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: distributed-replay
ms.reviewer: 
ms.suite: sql
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
caps.latest.revision: "8"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 397cb416c9c59482cf97be8e7554f5f2af7c2d7a
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="complete-the-post-installation-steps"></a>インストール後の手順の実行
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Distributed Replay をインストールした後は、分散再生コント ローラーおよびクライアント サービスのアカウントを変更する必要があります。  
  
### <a name="to-complete-the-post-installation-steps"></a>インストール後の手順を実行するには  
  
1.  **ファイアウォール ルールを作成する**: コントローラー コンピューターとクライアント コンピューターで、対応するサービスのファイアウォール経由の受信トラフィックを許可する必要があります。 インストール フォルダーに配置されているサービス実行可能ファイルのファイアウォール ルールを指定します。  
  
    1.  コントローラー サービスの場合は、インストール フォルダーにある **DReplayController.exe**のルールを作成します。 たとえば、次のコマンドを実行すると、このルールが有効になります ( `%InstallPath%` はサービスのインストール フォルダーです)。  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  クライアント サービスの場合は、クライアント コンピューターごとに、インストール フォルダーにある **DReplayClient.exe**のルールを作成します。 たとえば、次のコマンドを実行すると、このルールが有効になります ( `%InstallPath%` はサービスのインストール フォルダーです)。  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **対象サーバーで各クライアントの権限を与える**: クライアント コンピューターへのクライアント サービスのインストールが完了したら、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の対象インスタンスの sysadmin ロールにクライアント サービス アカウントを手動で追加する必要があります。  
  
## <a name="net-framework-security"></a>.NET Framework のセキュリティ  
 分散再生の機能をインストールするには、管理権限が必要です。 sysadmin 権限を持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのみが、テスト サーバーの sysadmin サーバー ロールにクライアント サービス アカウントを追加できます。 Distributed Replay のセキュリティ上の考慮事項の詳細については、「 [Distributed Replay のセキュリティ](../../tools/distributed-replay/distributed-replay-security.md)」を参照してください。  
  
  
