---
title: "[サブスクリプションの再初期化] - [すべてのサブスクリプション] | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
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
- sql13.rep.reinit.all.f1
helpviewer_keywords:
- Reinitialize Subscription(s) dialog box
ms.assetid: e1122018-9f74-43e3-8489-7eae33ff23d9
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5e5ca311380d3b6f1ce479ea816f71cd20fea752
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="reinitialize-subscriptions---all-subscriptions"></a>[サブスクリプションの再初期化] - [すべてのサブスクリプション]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[サブスクリプションの再初期化]** ダイアログ ボックスを使用すると、パブリケーションに対してすべてのサブスクリプションを再初期化するように設定できます。 再初期化には各サブスクライバーへのスナップショットの適用が伴います。再初期化は、トランザクション パブリケーションに対するサブスクリプションではディストリビューション エージェントによって実行され、マージ パブリケーションに対するサブスクリプションではマージ エージェントによって実行されます。  
  
## <a name="options"></a>および  
 **[現在のスナップショットを使用する]**  
 サブスクリプションに対してディストリビューション エージェントまたはマージ エージェントが次回実行されるとき、各サブスクライバーに現在のスナップショットを適用します。 有効なスナップショットが使用できない場合、このオプションは選択できません。  
  
 **[新しいスナップショットを使用する]**  
 すべてのサブスクリプションを新しいスナップショットで再初期化します。 スナップショットは、スナップショット エージェントによって生成された後でのみ、各サブスクライバーに適用できます。 スナップショット エージェントがスケジュールによって実行されるように設定されている場合、サブスクリプションは、次にスケジュールされているスナップショット エージェントが実行されるまで再初期化されません。  
  
 スナップショット エージェントをすぐに開始するには、 **[今すぐ新しいスナップショットを生成する]** を選択します。  
  
 **[再初期化する前に、同期されていない変更をアップロード]**  
 マージ レプリケーションのみです。 サブスクライバーのデータがスナップショットで上書きされる前に、サブスクリプション データベースのすべての保留中の変更をアップロードします。  
  
 パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。 保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。  
  
 **[再初期化するように設定]**  
 再初期化するために各サブスクリプションを設定します。 有効なスナップショットが使用できるようになった後、サブスクリプションに対してディストリビューション エージェントまたはマージ エージェントを次回実行するとき、スナップショットはサブスクライバーに適用されます。  
  
## <a name="see-also"></a>参照  
 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)  
  
  
