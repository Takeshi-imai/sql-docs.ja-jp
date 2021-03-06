---
title: "[サブスクリプションのプロパティ - サブスクライバー] | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.subproperties.subscriber.f1
helpviewer_keywords:
- Subscription Properties dialog box
ms.assetid: bef66929-3234-4a45-8ec4-3b271519d07a
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eb2d94f889cd593e07331f19fd09ef29d94479b8
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="subscription-properties---subscriber"></a>[サブスクリプションのプロパティ - サブスクライバー]
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  サブスクライバーの **[サブスクリプションのプロパティ]** ダイアログ ボックスを使用すると、プル サブスクリプションのプロパティを表示したり設定したりできます。  
  
 **[サブスクリプションのプロパティ]** ダイアログ ボックスの各プロパティには説明が含まれています。 プロパティをクリックすると、ダイアログ ボックスの一番下に説明が表示されます。 このトピックでは、いくつかのプロパティについて追加情報を示します。 プロパティは次のように分類されます。  
  
-   すべてのサブスクリプションに適用されるプロパティ。  
  
-   トランザクション サブスクリプションに適用されるプロパティ。  
  
-   マージ サブスクリプションに適用されるプロパティ。  
  
 読み取り専用として表示されているオプションの場合、サブスクリプションが作成されている場合にのみ設定できます。 サブスクリプションの新規作成ウィザードで使用することのできないオプションを設定する場合は、サブスクリプションをストアド プロシージャで作成します。 詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) 」および「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」を参照してください。  
  
> [!NOTE]  
>  ディストリビューション エージェントまたはマージ エージェントのジョブがサブスクリプションに対してまだ作成されていない場合、ほとんどのサブスクリプション プロパティは表示されません。 プル サブスクリプションのエージェント ジョブを作成するには、[sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) (スナップショットまたはトランザクション パブリケーションへのサブスクリプションの場合) または [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) (マージ パブリケーションへのサブスクリプションの場合) を実行します。  
  
## <a name="options-for-all-subscriptions"></a>すべてのサブスクリプションに対するオプション  
 **[スナップショットからパブリッシュされたデータを初期化]**  
 サブスクリプションがスナップショットで初期化されるか (既定)、別の方法で初期化されるかを決定します。 サブスクリプションの初期化の詳細については、「[サブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription.md)」を参照してください。  
  
 **[スナップショットの場所]**  
 初期化または再初期化の際にアクセスするスナップショット ファイルの場所を決定します。 場所は次の値のいずれかです。  
  
-   **[既定の場所]**: ディストリビューターの構成時に定義される既定の場所です。 詳細については、「[既定のスナップショットの場所の指定 &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)」を参照してください。  
  
-   **[代替フォルダー]**: **[パブリケーションのプロパティ]** ダイアログ ボックスで指定することができる代替の場所です。 詳細については、「 [Alternate Snapshot Folder Locations](../../relational-databases/replication/alternate-snapshot-folder-locations.md)」を参照してください。  
  
-   **[動的スナップショット フォルダー]**: パラメーター化された行フィルターを使用するマージ パブリケーションのスナップショットの場所です。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。  
  
-   **[FTP フォルダー]**: FTP (ファイル転送プロトコル) サーバーにアクセスできるフォルダーです。 詳細については、「[FTP によるスナップショットの転送](../../relational-databases/replication/transfer-snapshots-through-ftp.md)」を参照してください。  
  
 **[スナップショット フォルダー]**  
 **[スナップショットの場所]** オプションに対して **[既定の場所]** 以外の値を選択した場合、そのスナップショット フォルダーへのパスを指定する必要があります。  
  
 **[Windows 同期マネージャーを使用]**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 同期マネージャーを使用して、サブスクリプションを同期化できるかどうかを決定します。  
  
 **Security**  
 **[エージェント プロセス アカウント]** 行をクリックしてプロパティ ボタン (**[...]**) をクリックし、ディストリビューション エージェントまたはマージ エージェントがサブスクライバーで実行されるアカウントを変更します。 接続に関するセキュリティ オプションは、サブスクリプションの種類によって異なります。  
  
-   トランザクション パブリケーションへのサブスクリプションの場合、ディストリビューション エージェントがディストリビューターへの接続を作成するアカウントを変更するには、 **[ディストリビューター接続]**をクリックしてプロパティ ボタン (**[...]**) をクリックします。  
  
-   トランザクション パブリケーションへの即時更新サブスクリプションの場合、上記のディストリビューター接続に加え、サブスクライバーからパブリッシャーに変更を伝達するのに使用する方法を変更することができます。これを行うには、 **[パブリッシャー接続]**をクリックしてプロパティ ボタン (**[...]**) をクリックします。  
  
-   マージ パブリケーションへのサブスクリプションの場合、 **[パブリッシャー接続]**をクリックしてプロパティ ボタン (**[...]**) をクリックします。  
  
 各エージェントに必要な権限の詳細については、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
## <a name="options-for-transactional-subscriptions"></a>トランザクション サブスクリプションに対するオプション  
 **[更新可能なサブスクリプション]**  
 サブスクライバーの変更がパブリッシャーにレプリケートされるかどうかを決定します。 変更は、キュー更新または即時更新を使用してレプリケートすることができます。 **[サブスクライバーの更新方法]** オプションでは、どの方法を使用するかを決定します。 詳細については、「 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)」を参照してください。  
  
## <a name="options-for-merge-subscriptions"></a>マージ サブスクリプションに対するオプション  
 **[パーティション定義 (HOST_NAME)]**  
 パラメーター化されたフィルターを使用するパブリケーションの場合、マージ レプリケーションでは、同期化中に 2 つのシステム関数、 **SUSER_SNAME()** または **HOST_NAME()**のうちの 1 つ (フィルターが両方の関数を参照する場合は両方の関数) を評価して、サブスクライバーが受け取る必要のあるデータを決定します。 既定では、 **HOST_NAME()** は、マージ エージェントが実行されているコンピューターの名前を返しますが、この値はサブスクリプションの新規作成ウィザードで上書きすることができます。 パラメーター化されたフィルターと **HOST_NAME()**の上書きの詳細については、「 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」を参照してください。  
  
 **[サブスクリプションの種類]** と **[優先度]**  
 サブスクリプションがクライアント サブスクリプションまたはサーバー サブスクリプションであるかどうかを表示します (これは、サブスクリプションが作成された後では変更できません)。 サーバー サブスクリプションは、他のサブスクライバーへのデータの再パブリッシュと、競合解決方法の優先度の割り当てができます。  
  
 サブスクリプションの新規作成ウィザードでサーバーのサブスクリプションの種類を選択した場合、サブスクライバーには競合解決方法で使用される優先度が割り当てられます。  
  
 **[競合を対話的に解決する (対話的な解決をサポートするアーティクルに対してのみ適用されます)]**  
 インタラクティブ競合回避モジュールのユーザー インターフェイスを使用して、マージ同期中の競合を回避するかどうかを決定します。 これを行うには、 **[Windows 同期マネージャーを使用]** に **[有効化]**の値を設定する必要があります。 詳細については、「 [Interactive Conflict Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)」を参照してください。  
  
 **[Web 同期]**  
 **[Web 同期を使用]** では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) サーバーに接続してサブスクリプションを同期するかどうかを決定します。 このオプションは、パブリケーションに対して Web 同期が有効である場合のみ有効です。 詳細については、「 [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)」を参照してください。  
  
 **[Web 同期を使用]** に **[True]**を選択した場合、次の手順に従います。  
  
-   **[Web サーバー アドレス]**に IIS サーバーのフル アドレスを入力します。  
  
-   サブスクライバーが IIS サーバーに接続されるアカウントを設定または変更するには、 **[Web サーバー接続]** 行をクリックしてプロパティ ボタン (**[...]**) をクリックします。  
  
-   必要であれば、 **[Web サーバーのタイムアウト]** を変更します。 タイムアウトは Web 同期要求の期限が切れるまでの期間 (秒単位) です。  
  
 構成の詳細については、「 [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションのプロパティの表示または変更](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [プッシュ サブスクリプションのプロパティの表示または変更](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
