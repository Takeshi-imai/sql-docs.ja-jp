---
title: MSSQLSERVER_-1 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- "-1"
helpviewer_keywords:
- -1 (Database Engine error)
ms.assetid: bad25b91-eaed-46c0-a5b7-71117a32304c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 048db39c941cd54977c09450097724ebc7a2c584
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver-1"></a>MSSQLSERVER_-1
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|-1|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名||  
|メッセージ テキスト|サーバーへの接続を確立中にエラーが発生しました。  接続先が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] である場合、既定の設定では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリモート接続を許可していないために、このエラーが発生した可能性があります  (プロバイダー: SQL ネットワーク インターフェイス、エラー: 28 - サーバーは要求されたプロトコルをサポートしていません) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、エラー: -1)。|  
  
## <a name="explanation"></a>説明  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントがサーバーに接続できません。 このエラーは、次のいずれかの原因により起こる可能性があります。  
  
-   指定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス名が有効ではありません。  
  
-   TCP または名前付きパイプ プロトコルが有効ではありません。  
  
-   サーバー上のファイアウォールで接続が拒否されました。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービス (sqlbrowser) が開始されていません。  
  
## <a name="user-action"></a>ユーザーの操作  
このエラーを解決するには、以下のいずれかの操作を試してみます。  
  
-   接続文字列で指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス名のスペルを確認します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー ツールを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が TCP や名前付きパイプのプロトコルを経由したリモート接続を受け入れられるようにします。 リモート接続の受け入れの詳細については、「[サーバー ネットワーク プロトコルの有効化または無効化](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)」を参照してください。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサーバー インスタンスで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のポートおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser ポート (UDP 1434) を開くようにファイアウォールを構成していることを確認します。  
  
-   サーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが開始されていることを確認します。  
  
## <a name="see-also"></a>参照  
[データベース エンジン アクセスを有効にするための Windows ファイアウォールを構成する](~/database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
[クライアント プロトコルの構成](~/database-engine/configure-windows/configure-client-protocols.md)  
[ネットワーク プロトコルとネットワーク ライブラリ](~/sql-server/install/network-protocols-and-network-libraries.md)  
[クライアント ネットワーク構成](~/database-engine/configure-windows/client-network-configuration.md)  
[クライアント プロトコルの構成](~/database-engine/configure-windows/configure-client-protocols.md)  
[サーバー ネットワーク プロトコルの有効化または無効化](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
