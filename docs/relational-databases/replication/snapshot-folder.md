---
title: "[スナップショット フォルダー] | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d2b5d93b071795bad8e12481e670e0cefc8c57ed
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="snapshot-folder"></a>[スナップショット フォルダー]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ディストリビューションの構成ウィザードとパブリケーションの新規作成ウィザードには、 **[スナップショット フォルダー]** ページが表示されます。 このウィザードで有効にしたすべてのパブリッシャーでは、このページで指定したスナップショット フォルダーの場所が既定で使用されます (後から **[ディストリビューターのプロパティ]** ダイアログ ボックスを使用して有効にしたパブリッシャーには、この既定のスナップショット フォルダーが適用されません)。 ディストリビューションの構成ウィザードまたは **[ディストリビューターのプロパティ]** ダイアログ ボックスの **[パブリッシャー]** ページで、任意のパブリッシャーの既定のスナップショット フォルダーを変更できます。  
  
 スナップショット フォルダーは、共有として指定したディレクトリです。このフォルダーの読み取りと書き込みをするエージェントには、このフォルダーへのアクセスを可能にする十分な権限が必要です。 フォルダーの適切なセキュリティ保護の詳細については、「[Secure the Snapshot Folder](../../relational-databases/replication/security/secure-the-snapshot-folder.md)」(スナップショット フォルダーのセキュリティ保護) をご覧ください。 レプリケーションを実装する前に、レプリケーション エージェントがスナップショット フォルダーに接続できることをテストします。 各エージェントで使用されるアカウントを使用してログオンした後、スナップショット フォルダーへのアクセスを試行します。  
  
## <a name="options"></a>および  
 **Snapshot folder**  
 スナップショット ファイルを保存するフォルダーのパスを入力します。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] はスナップショット フォルダーの場所に、ネットワーク共有を使用することをお勧めします。 ローカル パス (C:\\ など、ドライブ文字で始まるパス) を使用した場合、他のコンピューター上のエージェントがアクセスできません。  
  
## <a name="see-also"></a>参照  
 [スナップショット フォルダーの代替位置](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)   
 [パブリッシングとディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
