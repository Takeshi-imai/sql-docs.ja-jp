---
title: "不明なサービス ([ログオン] タブ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9b35cb5-d8ae-42ea-b59e-deedc99c4823
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 429944b2499f1567b622d77a5cde15f698a9382d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="unknown-service-log-on-tab"></a>[不明なサービス] ダイアログ ボックス ([ログオン] タブ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、このサービスを識別できません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、サービスを実行しているコンピューターの WMI プロバイダーからそのサービスの情報を受け取ります。 そのサービスのプロパティの読み取り中にエラーが発生したか、そのサービスのプロパティに不備がありました。 この問題を解決するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーをいったん閉じてから再び開くか、そのサービスを実行しているコンピューターの WMI プロバイダーをチェックします。  
  
 WMI プロバイダーは、Windows のコンポーネントです。 WMI プロバイダーの権限をチェックする方法については、SQL Server オンライン ブックの「SQL Server ツールでサーバーの状態を表示できるように WMI を構成する方法」を参照してください。  
  
 適切なサービスを表示していると確信できる場合は、 **[不明なサービス]** ダイアログ ボックスの **[ログオン]** タブで、そのサービスが使用するアカウントの指定や、そのサービスの開始と停止を行います。  
  
## <a name="options"></a>オプション  
 **[ローカル システム アカウント]**  
 ローカル システム アカウントを指定します。このアカウントはパスワードを必要としません。 ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスが他のサーバーと対話できないこともあります。  
  
 **[このアカウント]**  
 Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。 サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。 アカウントの選択の詳細については、オンライン ブックの「Windows サービス アカウントの設定」を参照してください。  
  
 **アカウント名**  
 ローカル ユーザー アカウント名またはドメイン ユーザー アカウント名を指定します。  
  
 **Password**  
 アカウントのパスワードを入力します。  
  
 **[パスワードの確認入力]**  
 アカウントのパスワードを再度入力します。  
  
 **コントロール パネルの  ◆セグ : 文が分断されているため、訳の位置が入れ替わっています◇**  
 サービスを開始します。  
  
 **[停止]**  
 サービスを停止します。  
  
 **[一時停止]**  
 サービスを一時停止します。  
  
 **[再開]**  
 一時停止したサービスを再開します。  
  
  
