---
title: "レッスン 2 : トランザクション パブリケーションへのサブスクリプションの作成 | Microsoft Docs"
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
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 5995b7d2-7c06-46f5-b96c-2bee879bcda2
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 54dd4030aa4212f23b1ccaf3f5b3a19ca8fc0f48
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="lesson-2-creating-a-subscription-to-the-transactional-publication"></a>レッスン 2 : トランザクション パブリケーションへのサブスクリプションの作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
このレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してサブスクリプションを作成します。 このレッスンを薦めるには、前のレッスンである「 [レッスン 1: トランザクション レプリケーションを使用したデータのパブリッシュ](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md)」を完了している必要があります。  
  
### <a name="to-create-the-subscription"></a>サブスクリプションを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続して、サーバー ノードを展開し、 **[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、 **[AdvWorksProductTrans]** パブリケーションを右クリックして、 **[新しいサブスクリプション]**をクリックします。  
  
    サブスクリプションの新規作成ウィザードが起動します。  
  
3.  [パブリケーション] ページで **[AdvWorksProductTrans]**を選択し、 **[次へ]**をクリックします。  
  
4.  [ディストリビューション エージェントの場所] ページで、 **[ディストリビューターですべてのエージェントを実行する]**を選択し、 **[次へ]**をクリックします。  
  
5.  [サブスクライバー] ページにサブスクライバー インスタンスの名前が表示されない場合は、**[サブスクライバーの追加]**、**[SQL Server サブスクライバーの追加]** の順にクリックし、**[サーバーの接続]** ダイアログ ボックスにサブスクライバー インスタンス名を入力して、**[接続]** をクリックします。  
  
6.  [サブスクライバー] ページでサブスクライバー サーバーのインスタンス名を選択し、**[サブスクリプション データベース]** で **[<New Database>]** を選択します。  
  
7.  **[新しいデータベース]** ダイアログ ボックスで、 **[データベース名]** ボックスに「 **ProductReplica** 」と入力し、 **[OK]**をクリックして **[次へ]**をクリックします。  
  
8.  **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスで、参照ボタン (**[…]**) をクリックし、**[プロセス アカウント]** ボックスに「\<*コンピューター名>***\repl_distribution**」と入力します。次に、このアカウントのパスワードを入力して **[OK]** をクリックし、**[次へ]** をクリックします。  
  
9. 以降のページでは既定値をそのまま採用し、 **[完了]** をクリックしてウィザードを終了します。  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>サブスクライバー側のデータベース権限を設定するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続します。次に、 **[データベース]**、 **[ProductReplica]**、 **[セキュリティ]**の順に展開し、 **[ユーザー]**を右クリックして、 **[新しいユーザー]**をクリックします。  
  
2.  **[全般]** ページの **[ユーザーの種類]** ボックスの一覧の **[Windows ユーザー]** をクリックします。  
  
3.  **[ユーザー名]** ボックスを選択し、**[選択するオブジェクト名を入力してください]** ボックスに「<Machine_Name>**\repl_distribution**」と入力し、**[名前の確認]** をクリックして、**[OK]** をクリックします。  
  
4.  **[メンバーシップ]** ページの **[データベース ロールのメンバーシップ]** 領域で、**[db_owner]** を選択し、**[OK]** をクリックしてユーザーを作成します。  
  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a>サブスクリプションの同期状態を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続して、サーバー ノードを展開し、 **[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーで、 **AdvWorksProductTrans** パブリケーションを展開し、 **ProductReplica** データベースのサブスクリプションを右クリックして、 **[同期の状態の表示]**をクリックします。  
  
    サブスクリプションの現在の同期状態が表示されます。  
  
3.  **[AdvWorksProductTrans]**の下にサブスクリプションが表示されない場合は、F5 キーを押して一覧を更新します。  
  
## <a name="next-steps"></a>Next Steps  
ここでは、トランザクション パブリケーションへのサブスクリプションを作成しました。 このサブスクリプションのディストリビューション エージェントは常時動作しているので、サブスクリプションの作成時に初期化も行われます。 次は、トレーサー トークンを使って、変更内容がサブスクライバーにレプリケートされているかどうかを確認し、待機時間を決定します。 「 [レッスン 3: サブスクリプションの検証と待機時間の計測](../../relational-databases/replication/lesson-3-validating-the-subscription-and-measuring-latency.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)  
[パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
