---
title: "前提条件、制限事項、推奨事項 - Always On 可用性グループ | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], WSFC clusters
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], Failover Cluster Instances
- Availability Groups [SQL Server], databases
- Availability Groups [SQL Server]
ms.assetid: edbab896-42bb-4d17-8d75-e92ca11f7abb
caps.latest.revision: "151"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Active
ms.openlocfilehash: d127b3479e6bb38483d39556884d1498d9c662c2
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="prereqs-restrictions-recommendations---always-on-availability-groups"></a>前提条件、制限事項、推奨事項 - Always On 可用性グループ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  このトピックでは、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の展開に関して、各種コンポーネント (ホスト コンピューター、Windows Server フェールオーバー クラスタリング (WSFC)、サーバー インスタンス、可用性グループ) の前提条件、制限、推奨事項などの考慮事項について説明します。 各コンポーネントのセキュリティに関する考慮事項のほか、要求される権限 (該当する場合) にも触れています。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を配置する前に、このトピックのすべてのセクションを読むことを強くお勧めします。  
    
##  <a name="DotNetHotfixes"></a> 可用性グループをサポートする .Net 修正プログラム  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で使用する [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]コンポーネントと機能によっては、次の表で指定されている追加の .Net 修正プログラムのインストールが必要になる場合があります。 これらの修正プログラムは任意の順序でインストールできます。  
  
||依存機能|修正プログラム|リンク|  
|------|-----------------------|------------|----------|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]|.Net 3.5 SP1 の修正プログラムは、SQL クライアントに読み取り目的、読み取り専用、multisubnetfailover の Always On 機能のサポートを追加します。 修正プログラムは、各 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] レポート サーバーにインストールする必要があります。|KB 2654347: [Always On 機能のサポートを追加する .Net 3.5 SP1 の修正プログラム](http://go.microsoft.com/fwlink/?LinkId=242896)|  
  
##  <a name="SystemReqsForAOAG"></a> Windows のシステム要件と推奨事項  
 **このセクションの内容**  
  
-   [チェック リスト: 要件](#SystemRequirements)  
  
-   [可用性レプリカをホストするコンピューターに関する推奨事項 (Windows システム)](#ComputerRecommendations)  
  
-   [アクセス許可](#PermissionsWindows)  
  
-   [関連タスク](#RelatedTasksWindows)  
  
-   [関連コンテンツ](#RelatedContentWS)  
  
###  <a name="SystemRequirements"></a> チェック リスト: 要件 (Windows システム)  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の機能を利用するには、1 つまたは複数の可用性グループに参加するすべてのコンピューターが、次の基本要件を満たしている必要があります。  
  
||要件|リンク|  
|------|-----------------|----------|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|システムがドメイン コントローラーではないことを確認します。|可用性グループは、ドメイン コントローラーではサポートされていません。|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|すべてのコンピューターで Windows Server 2012 以降のバージョンが実行されていることを確認します。|[SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|各コンピューターが WSFC のノードであることを確認します。|[Windows Server フェールオーバー クラスタリング &#40;WSFC&#41; と SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|必要な可用性グループの構成に耐える十分なノードが WSFC に存在することを確認します。|クラスター ノードは、1 つの可用性グループにつき 1 つだけ可用性レプリカをホストすることができます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスは、特定のクラスター ノード上で複数の可用性グループの可用性レプリカをホストできます。<br /><br /> 予定している可用性グループの可用性レプリカをサポートするために必要なクラスター ノードの数については、データベース管理者にお問い合わせください。<br /><br /> [Always On 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)。|  
  
> [!IMPORTANT]  
>  可用性グループへの接続に必要な構成が環境に対して正しく実施されていることも確認します。 詳細については、「 [Always On クライアント接続 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-client-connectivity-sql-server.md)。  
  
###  <a name="ComputerRecommendations"></a> 可用性レプリカをホストするコンピューターに関する推奨事項 (Windows システム)  
  
-   **同程度のシステム:**  可用性グループ内の可用性レプリカはすべて、ワークロードの処理能力が同程度であるシステム上で運用する必要があります。  
  
-   **専用のネットワーク アダプター:**  最適なパフォーマンスを得るには、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]に専用のネットワーク アダプター (ネットワーク インターフェイス カード) を使用します。  
  
-   **十分なディスク領域:**  可用性レプリカをホストするサーバー インスタンスのあるすべてのコンピューターには、可用性グループ内のすべてのデータベースを格納できるだけのディスク領域が存在する必要があります。 プライマリ データベースが大きくなるにつれて、対応するセカンダリ データベースも同じだけ大きくなる点に注意してください。  
  
###  <a name="PermissionsWindows"></a> 権限 (Windows システム)  
 WSFC を管理するユーザーは、すべてのクラスター ノードのシステム管理者であることが必要です。  
  
 クラスターを管理するためのアカウントの詳細については、「 [付録 A: フェールオーバー クラスターの要件](http://technet.microsoft.com/library/dd197454.aspx)」を参照してください。  
  
###  <a name="RelatedTasksWindows"></a> 関連タスク (Windows システム)  
  
|タスク|リンク|  
|----------|----------|  
|HostRecordTTL の値を設定します。|[HostRecordTTL の変更 (Windows PowerShell を使用)](#ChangeHostRecordTTLps)|  
  
####  <a name="ChangeHostRecordTTLps"></a> HostRecordTTL の変更 (Windows PowerShell を使用)  
  
1.  **[管理者として実行]**を選択して PowerShell ウィンドウを開きます。  
  
2.  FailoverClusters モジュールをインポートします。  
  
3.  **Get-ClusterResource** コマンドレットを使用してネットワーク名リソースを検索し、次に **Set-ClusterParameter** コマンドレットを使用して **HostRecordTTL** 値を設定します。次に例を示します。  
  
     Get-ClusterResource “*\<NetworkResourceName>*” | Set-ClusterParameter HostRecordTTL *\<TimeInSeconds>*  
  
     次に示す PowerShell の例では、`SQL Network Name (SQL35)` というネットワーク名リソースの HostRecordTTL を 300 秒に設定します。  
  
    ```  
    Import-Module FailoverClusters  
  
    $nameResource = "SQL Network Name (SQL35)"  
    Get-ClusterResource $nameResource | Set-ClusterParameter ClusterParameter HostRecordTTL 300  
    ```  
  
    > [!TIP]  
    >  新しい PowerShell ウィンドウを開くたびに、 **FailoverClusters** モジュールをインポートする必要があります。  
  
##### <a name="related-content-powershell"></a>関連コンテンツ (PowerShell)  
  
-   [クラスターと高可用性](http://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (フェールオーバー クラスタリングとネットワーク負荷分散のチームのブログ)  
  
-   [フェールオーバー クラスターの Windows PowerShell の概要](http://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [クラスター リソースのコマンドと同等の Windows PowerShell コマンドレット](http://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
###  <a name="RelatedContentWS"></a> 関連コンテンツ (Windows システム)  
  
-   [マルチサイト フェールオーバー クラスターの DNS 設定を構成する](http://technet.microsoft.com/library/dd197562\(WS.10\).aspx)  
  
-   [ネットワーク名リソースを使用した DNS 登録](http://blogs.msdn.com/b/clustering/archive/2009/07/17/9836756.aspx)  
  

##  <a name="ServerInstance"></a> SQL Server インスタンスの前提条件と制限  
 可用性グループにはそれぞれ、 *のインスタンスによってホストされる一連のフェールオーバー パートナー (*可用性レプリカ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) が必要です。 サーバー インスタンスには、 *スタンドアロン インスタンス* または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]*フェールオーバー クラスター インスタンス* (FCI) を使用できます。  
  
 **このセクションの内容**  
  
-   [チェック リスト: 前提条件](#PrerequisitesSI)  
  
-   [可用性グループによるスレッドの使用](#ThreadUsage)  
  
-   [アクセス許可](#PermissionsSI)  
  
-   [関連タスク](#RelatedTasksSI)  
  
-   [関連コンテンツ](#RelatedContentSI)  
  
###  <a name="PrerequisitesSI"></a> チェック リスト: 前提条件 (サーバー インスタンス)  
  
||前提条件|リンク|  
|-|------------------|-----------|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|このホスト コンピューターは WSFC ノードである必要があります。 可用性グループの可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスは、クラスターの別のノードに存在します。 別のクラスターに移行するときに、可用性グループは一時的に 2 つのクラスターにまたがることができます。 SQL Server 2016 には分散型可用性グループが導入されています。 分散型可用性グループでは、2 つの可用性グループが別々のクラスターに存在します。|[Windows Server フェールオーバー クラスタリング &#40;WSFC&#41; と SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)<br /><br /> [フェールオーバー クラスタリングと Always On 可用性グループ &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)<br/> <br/> [分散型可用性グループ (Always On 可用性グループ)](../../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|可用性グループで Kerberos を操作するには:<br /><br /> 可用性グループの可用性レプリカをホストするすべてのサーバー インスタンスで、同じ SQL Server サービス アカウントを使用する必要があります。<br /><br /> ドメイン管理者は、可用性グループ リスナーの仮想ネットワーク名 (VNN) の SQL Server サービス アカウントに、Active Directory でサーバー プリンシパル名 (SPN) を手動で登録する必要があります。 SQL Server サービス アカウント以外のアカウントに SPN が登録されている場合は、認証が失敗します。<br /><br /> <br /><br /> **\*\* 重要 \*\*** SQL Server サービス アカウントを変更した場合は、ドメイン管理者が SPN を手動で再登録する必要があります。|[Kerberos 接続用のサービス プリンシパル名の登録](../../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)<br /><br /> **簡単な説明:**<br /><br /> Kerberos と SPN は相互認証を行います。 SPN は、SQL Server サービスを起動する Windows アカウントにマップされます。 SPN が正常に登録されていないか登録に失敗した場合、Windows セキュリティ レイヤーは、SPN に関連するアカウントを決定することができず、Kerberos 認証は使用できません。<br /><br /> <br /><br /> 注: NTLM には、この要件はありません。|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンス (FCI) を使用して可用性レプリカをホストする予定がある場合は、FCI の制限を確実に理解し、FCI の要件が満たされていることを確認してください。|[SQL Server のフェールオーバー クラスター インスタンス (FCI) を使用して可用性レプリカをホストするための前提条件と要件](#FciArLimitations) (このトピックの後半)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|すべてのサーバー インスタンスで Enterprise Edition の [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]が実行されている必要があります。|[SQL Server 2016 の各エディションとサポートされる機能](../../../sql-server/editions-and-supported-features-for-sql-server-2016.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|特定の可用性グループの可用性レプリカをホストするすべてのサーバー インスタンス間で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の照合順序を統一する必要があります。|[サーバーの照合順序の設定または変更](../../../relational-databases/collations/set-or-change-the-server-collation.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|可用性グループの可用性レプリカをホストするすべてのサーバー インスタンスで [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 機能を有効にします。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のサーバー インスタンスは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 環境がサポートする範囲内であれば、1 台のコンピューターでいくつでも有効にすることができます。|[AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)<br /><br /> <br /><br /> **\*\* 重要 \*\*** WSFC を破棄してから再作成した場合は、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を有効にしていた、元のクラスター上の各サーバー インスタンスについて、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 機能を無効にしてからもう一度有効にする必要があります。|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|すべてのサーバー インスタンスには、データベース ミラーリング エンドポイントが必要です。 このエンドポイントは、サーバー インスタンス上のミラーリング監視サーバーとデータベース ミラーリング パートナー、および可用性レプリカすべてによって共有されます。<br /><br /> 可用性レプリカのホストとして選んだサーバー インスタンスがドメイン ユーザー アカウントで実行されていて、まだデータベース ミラーリング エンドポイントが存在しない場合、 [新しい可用性グループ ウィザード](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md) (または [可用性グループへのレプリカの追加ウィザード](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)) でエンドポイントを作成し、サーバー インスタンス サービス アカウントに CONNECT 権限を許可することができます。 ただし、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスがビルトイン アカウント (Local System、Local Service、Network Service など) で実行されている場合または非ドメイン アカウントで実行されている場合は、エンドポイント認証に証明書を使用する必要があります。ウィザードは、サーバー インスタンス上でデータベース ミラーリング エンドポイントを作成できなくなります。 この場合は、データベース ミラーリング エンドポイントを手動で作成してからウィザードを起動することをお勧めします。<br /><br /> <br /><br /> **\*\* セキュリティに関する注意 \*\*** [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のトランスポート セキュリティは、データベース ミラーリングと同じです。|[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)<br /><br /> [データベース ミラーリングと Always On 可用性グループのトランスポート セキュリティ &#40;SQL Server&#41;](../../../database-engine/database-mirroring/transport-security-database-mirroring-always-on-availability.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|FILESTREAM を使用するデータベースを可用性グループに追加する場合は、その可用性グループの可用性レプリカをホストするすべてのサーバー インスタンスで FILESTREAM が有効になっていることを確認してください。|[FILESTREAM の有効化と構成](../../../relational-databases/blob/enable-and-configure-filestream.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|包含データベースを可用性グループに追加する場合は、その可用性グループの可用性レプリカをホストするすべてのサーバー インスタンスで **contained database authentication** サーバー オプションが **1** に設定されていることを確認してください。|[contained database authentication サーバー構成オプション](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md)<br /><br /> [サーバー構成オプション &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)|  
  
###  <a name="ThreadUsage"></a> 可用性グループによるスレッドの使用  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] には、ワーカー スレッドに関する次の要件があります。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のアイドル状態のインスタンスでは、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] はスレッドを使用しません。  
  
-   可用性グループが使用するスレッドの最大数は、サーバー スレッドの最大数 ('**max worker threads**') から 40 を引いた数にあらかじめ設定されています。  
  
-   特定のサーバー インスタンスでホストされる可用性レプリカは 1 つのスレッド プールを共有します。  
  
     スレッドは、次のように要求に基づいて共有されます。  
  
    -   通常は 3 ～ 10 個の共有スレッドがありますが、プライマリ レプリカのワークロードに応じてこの数が増える場合があります。  
  
    -   特定のスレッドが一定期間アイドル状態になると、そのスレッドは解放され、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の汎用スレッド プールに戻されます。 通常、非アクティブ スレッドは、非アクティブな状態のまま最大 15 秒経過すると解放されます。 ただし、最後の利用状況によっては、アイドル状態のスレッドが保持される時間が延長される場合があります。  

    - SQL Server インスタンスは、セカンダリ レプリカの並列再実行に最大で 100 個のスレッドを使用します。 各データベースは、最大で、CPU コアの合計数の半分を使用しますが、データベースあたりのスレッド数は 16 個以下となります。 単一のインスタンスで必要なスレッド数の合計が 100 を超えている場合、SQL Server は、残りの各データベースには単一の再実行スレッドを使用します。 再実行スレッドは、非アクティブな状態のまま最大 15 秒経過すると解放されます。 

  
-   さらに、可用性グループでは非共有スレッドを次のように使用します。  
  
    -   各プライマリ レプリカでは、プライマリ データベースごとにログ キャプチャ スレッドを 1 つ使用します。 また、セカンダリ データベースごとにログ送信スレッドを 1 つ使用します。 ログ送信スレッドは、非アクティブな状態のまま最大 15 秒経過すると解放されます。    
  
    -   セカンダリ レプリカでのバックアップでは、バックアップ操作の間、プライマリ レプリカにスレッドが保持されます。  
  
 詳細については、「 [Always On - HADRON 学習シリーズ: HADRON 対応データベースのワーカー プールの使用](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx) 」(CSS [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エンジニアのブログ) をご覧ください。  
  
###  <a name="PermissionsSI"></a> 権限 (サーバー インスタンス)  
  
|タスク|必要な権限|  
|----------|--------------------------|  
|データベース ミラーリング エンドポイントを作成する|CREATE ENDPOINT 権限、または **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  また、CONTROL ON ENDPOINT 権限も必要です。 詳細については、「 [GRANT (エンドポイントの権限の許可) &#40;Transact-SQL&#41;](../../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)」を参照してください。|  
|有効にする [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]|ローカル コンピューターの **Administrator** グループのメンバーシップおよび WSFC に対するフル コントロール権限が必要です。|  
  
###  <a name="RelatedTasksSI"></a> 関連タスク (サーバー インスタンス)  
  
|タスク|トピック|  
|----------|-----------|  
|データベース ミラーリング エンドポイントが存在するかどうかを確認する|[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)|  
|データベース ミラーリング エンドポイントを作成する (まだ存在しない場合)|[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)<br /><br /> [データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)<br /><br /> [AlwaysOn 可用性グループのデータベース ミラーリング エンドポイントの作成 &#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/database-mirroring-always-on-availability-groups-powershell.md)|  
|可用性グループを有効にする|[Always On 可用性グループの有効化と無効化 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)|  
  
###  <a name="RelatedContentSI"></a> 関連コンテンツ (サーバー インスタンス)  
  
-   [Always On - HADRON 学習シリーズ: HADRON 対応データベースのワーカー プールの使用](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
##  <a name="NetworkConnect"></a> ネットワーク接続の推奨事項  
 WSFC ノード間の通信と、可用性レプリカ間の通信には、同じネットワーク リンクを使用することを強くお勧めします。  別々のネットワーク リンクを使用すると、一部のリンクにエラーが発生した場合に (断続的なエラーであっても)、予期しない動作が発生する可能性があります。  
  
 たとえば、自動フェールオーバーをサポートする可用性グループでは、自動フェールオーバー パートナーであるセカンダリ レプリカの状態が SYNCHRONIZED である必要があります。 このセカンダリ レプリカへのネットワーク リンクにエラーが発生した場合 (断続的なエラーであっても)、レプリカが UNSYNCHRONIZED 状態になり、リンクが復元されるまで再同期を開始できません。 セカンダリ レプリカが非同期状態にある間に WSFC が自動フェールオーバーを要求しても、自動フェールオーバーは行われません。  
  
##  <a name="ClientConnSupport"></a> クライアント接続のサポート  
 クライアント接続に関する [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のサポートについては、「 [Always On クライアント接続 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-client-connectivity-sql-server.md)。  
  
##  <a name="FciArLimitations"></a> SQL Server のフェールオーバー クラスター インスタンス (FCI) を使用して可用性レプリカをホストするための前提条件と制限  
 **このセクションの内容**  
  
-   [制限](#RestrictionsFCI)  
  
-   [チェック リスト: 前提条件](#PrerequisitesFCI)  
  
-   [関連タスク](#RelatedTasksFCIs)  
  
-   [関連コンテンツ](#RelatedContentFCIs)  
  
###  <a name="RestrictionsFCI"></a> 制限 (FCI)  
  
> [!NOTE]  
> フェールオーバー クラスター インスタンスは、クラスター化共有ボリューム (CSV) をサポートしています。 CSV の詳細については、「 [フェールオーバー クラスターのクラスターの共有ボリュームについて](http://technet.microsoft.com/library/dd759255.aspx)」を参照してください。  
  
-   **FCI のクラスター ノードでホストできるレプリカは、特定の可用性グループに対して 1 つだけである:** FCI に可用性レプリカを追加する場合、FCI の有効な所有者である WSFC ノードで、同じ可用性グループに対して別のレプリカをホストすることはできません。  
  
     さらに、その他の各レプリカは、同じ Windows Server フェールオーバー クラスター内の別のクラスター ノードに存在する SQL Server 2016 のインスタンスによってホストされている必要があります。 唯一の例外は、別のクラスターに移行するときに、可用性グループは一時的に 2 つのクラスターにまたがることができるという点です。  
  
-   **可用性グループによる自動フェールオーバーは FCI ではサポートされない:**  FCI は可用性グループによる自動フェールオーバーをサポートしないため、FCI によってホストされる可用性レプリカは手動フェールオーバー用にのみ構成できます。  
  
-   **FCI ネットワーク名の変更:**  可用性レプリカがホストされている FCI のネットワーク名を変更する必要がある場合、レプリカをその可用性グループから削除してから再度、可用性グループに追加する必要があります。 プライマリ レプリカを削除することはできません。そのため、プライマリ レプリカがホストされている FCI の名前を変更するには、セカンダリ レプリカにフェールオーバーしてから、以前のプライマリ レプリカを削除し、再度追加する必要があります。 FCI の名前を変更すると、そのデータベース ミラーリング エンドポイントの URL が変わる可能性があります。 レプリカを追加する際は、必ず最新のエンドポイントの URL を指定してください。  
  
###  <a name="PrerequisitesFCI"></a> チェック リスト: 前提条件 (FCI)  
  
||前提条件|リンク|  
|-|------------------|----------|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|標準の SQL Server フェールオーバー クラスター インスタンスのインストールと同様、各 SQL Server フェールオーバー クラスター インスタンス (FCI) が必要な共有ストレージを所有していることを確認してください。||  
  
###  <a name="RelatedTasksFCIs"></a> 関連タスク (FCI)  
  
|タスク|トピック|  
|----------|-----------|  
|SQL Server フェールオーバー クラスターのインストール|[新しい SQL Server フェールオーバー クラスターの作成 &#40;セットアップ&#41;](../../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)|  
|既存の SQL Server フェールオーバー クラスターのインプレース アップグレード|[SQL Server フェールオーバー クラスター インスタンスのアップグレード &#40;セットアップ&#41;](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md)|  
|既存の SQL Server フェールオーバー クラスターのメンテナンス|[SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;セットアップ&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)|  
  
###  <a name="RelatedContentFCIs"></a> 関連コンテンツ (FCI)  
  
-   [フェールオーバー クラスタリングと可用性グループ &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)  
  
-   [Always On アーキテクチャ ガイド: フェールオーバー クラスター インスタンスと可用性グループの使用による高可用性および障害復旧ソリューションの構築](http://technet.microsoft.com/library/jj215886.aspx)  
  
##  <a name="PrerequisitesForAGs"></a> 可用性グループの前提条件と制限  
 **このセクションの内容**  
  
-   [制限](#RestrictionsAG)  
  
-   [必要条件](#RequirementsAG)  
  
-   [セキュリティ](#SecurityAG)  
  
-   [関連タスク](#RelatedTasksAGs)  
  
###  <a name="RestrictionsAG"></a> 制限 (可用性グループ)  
  
-   **可用性レプリカは、1 つの WSFC の別々のノードによってホストされている必要がある:**  各可用性グループで、個々の可用性レプリカは、同じ WSFC の別々のノード上で動作するサーバー インスタンスによってホストされる必要があります。 唯一の例外は、別のクラスターに移行するときに、可用性グループは一時的に 2 つのクラスターにまたがることができるという点です。  
  
    > [!NOTE]  
    >  同じ物理コンピューター上の各仮想コンピューターは独立したコンピューターとして動作するため、同じ可用性グループの可用性レプリカをそれぞれの仮想コンピューターがホストできます。  
  
-   **一意の可用性グループ名:**  各可用性グループの名前は、WSFC 上で一意である必要があります。 可用性グループ名の最大文字数は 128 文字です。  
  
-   **可用性レプリカ:**  各可用性グループは、1 つのプライマリ レプリカと最大 8 つのセカンダリ レプリカをサポートします。 すべてのレプリカを非同期コミット モードで実行することも、最大 3 つのレプリカを同期コミット モードで実行することもできます (1 つのプライマリ レプリカと 2 つの同期セカンダリ レプリカ)。  
  
-   **コンピューターあたりの可用性グループおよび可用性データベースの最大数:** コンピューター (VM または物理コンピューター) に実際に配置できるデータベースおよび可用性グループの数はハードウェアとワークロードによって異なりますが、強制的な制限はありません。 マイクロソフトでは、物理コンピューターあたり 10 の AG と 100 の DB を使用して広範なテストを行いました。 過剰な負荷がかかっているシステムには、ワーカー スレッドの枯渇、可用性グループ システム ビューおよび DMV の応答の遅延、ディスパッチャー システム ダンプの一時停止などの症状があります (ただし、これだけではありません)。 アプリケーション SLA 内でピーク ワークロード容量を処理できることを確認するために、実稼働環境と同様のワークロードを使用して環境を十分にテストしてください。 SLA を検討する際は、障害条件下の負荷や期待される応答時間を考慮してください。  
  
-   **フェールオーバー クラスター マネージャーを使用して可用性グループを操作しないでください。**  
  
     例 :  
  
    -   可用性グループのプロパティ (たとえば、有効な所有者) を変更しないでください。  
  
    -   フェールオーバー クラスター マネージャーを使用して可用性グループをフェールオーバーしないでください。 [!INCLUDE[tsql](../../../includes/tsql-md.md)] または [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]を使用する必要があります。  
  
###  <a name="RequirementsAG"></a> 前提条件 (可用性グループ)  
 可用性グループの構成を作成したり再構成したりする場合は、次の要件を満たす必要があります。  
  
||前提条件|Description|  
|-|------------------|-----------------|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンス (FCI) を使用して可用性レプリカをホストする予定がある場合は、FCI の制限を確実に理解し、FCI の要件が満たされていることを確認してください。|[SQL Server のフェールオーバー クラスター インスタンス (FCI) を使用して可用性レプリカをホストするための前提条件と制限](#FciArLimitations) (このトピックの前半)|  
  
###  <a name="SecurityAG"></a> セキュリティ (可用性グループ)  
  
-   セキュリティは WSFC から継承されます。 Windows Server フェールオーバー クラスタリングには、クラスター全体の粒度で 2 レベルのユーザー セキュリティがあります。  
  
    -   読み取り専用アクセス  
  
    -   フル コントロール  
  
         [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] はフル コントロールを必要とします。また、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を有効にした [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスには、クラスターのフル コントロール権限が (サービス SID を介して) 与えられます。  
  
         サーバー インスタンスのセキュリティをクラスター マネージャーで直接追加したり削除したりすることはできません。 クラスター セキュリティ セッションを管理するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーまたはそれに相当する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の WMI を使用します。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の各インスタンスには、レジストリやクラスターにアクセスするための権限が必要です。  
  
-   [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 可用性レプリカをホストするサーバー インスタンス間の接続は暗号化するようにお勧めします。  
  
#### <a name="permissions-availability-groups"></a>権限 (可用性グループ)  
  
|タスク|必要な権限|  
|----------|--------------------------|  
|可用性グループの作成|**sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。|  
|可用性グループの変更|可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。<br /><br /> さらに、データベースを可用性グループに参加させるには、 **db_owner** 固定データベース ロールのメンバーシップが必要です。|  
|可用性グループの削除|可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。 ローカル レプリカの場所でホストされていない可用性グループを削除するには、その可用性グループ上の CONTROL SERVER 権限または CONTROL 権限が必要です。|  
  
###  <a name="RelatedTasksAGs"></a> 関連タスク (可用性グループ)  
  
|タスク|トピック|  
|----------|-----------|  
|可用性グループの作成|[可用性グループ (新しい可用性グループ ウィザード)](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)<br /><br /> [可用性グループの作成 (Transact-SQL)](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)<br /><br /> [可用性グループの作成 (SQL Server PowerShell)](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)<br /><br /> [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)|  
|可用性レプリカの数の変更|[可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> [可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
|可用性グループ リスナーの作成|[可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)|  
|可用性グループの削除|[可用性グループの削除 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md)|  
  
##  <a name="PrerequisitesForDbs"></a> 可用性データベースの前提条件と制限  
 可用性グループに追加するデータベースは、次の前提条件と制限を満たしている必要があります。  
  
 **このセクションの内容**  
  
-   [必要条件](#RequirementsDb)  
  
-   [制限](#RestrictionsDb)  
  
-   [可用性レプリカをホストするコンピューターに関する推奨事項 (Windows システム)](#TDEdbs)  
  
-   [アクセス許可](#PermissionsDbs)  
  
-   [関連タスク](#RelatedTasksADb)  
  
###  <a name="RequirementsDb"></a> チェック リスト: 要件 (可用性データベース)  
 可用性グループに追加するデータベースは、次の条件を満たしている必要があります。  
  
||必要条件|リンク|  
|-|------------------|----------|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|ユーザー データベースであること。 システム データベースを可用性グループに追加することはできません。||  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|可用性グループの作成先となる [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス上に存在し、そのサーバー インスタンスからアクセスできること。||  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|読み取り/書き込み可能なデータベースであること。 読み取り専用データベースを可用性グループに追加することはできません。|[sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) (**is_read_only** = 0)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|マルチユーザー データベースであること。|[sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) (**user_access** = 0)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|AUTO_CLOSE が使用されていないこと。|[sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) (**is_auto_close_on** = 0)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|完全復旧モデル (完全復旧モードとも呼ばれます) を使用すること。|[sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) (**recovery_model** = 1)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|データベースの完全バックアップが少なくとも 1 つ存在すること。<br /><br /> 注: データベースを完全復旧モードに設定した後、完全復旧ログ チェーンを開始するには完全バックアップが必要です。|[データベースの完全バックアップの作成 &#40;SQL Server&#41;](../../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|既存の可用性グループに属していないこと。|[sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) (**group_database_id** = NULL)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|データベース ミラーリング用に構成されていないこと。|[sys.database_mirroring](../../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md) (データベースがミラー化の対象となっていない場合、"mirroring_" で始まるすべての列は NULL)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|FILESTREAM を使用するデータベースを可用性グループに追加する前に、その可用性グループの可用性レプリカをホストしている (またはこれからホストする) すべてのサーバー インスタンスで FILESTREAM が有効になっていることを確認してください。|[FILESTREAM の有効化と構成](../../../relational-databases/blob/enable-and-configure-filestream.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|包含データベースを可用性グループに追加する前に、その可用性グループの可用性レプリカをホストしている (またはこれからホストする) 各サーバー インスタンスで、 **contained database authentication** サーバー オプションが **1** に設定されていることを確認してください。|[contained database authentication サーバー構成オプション](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md)<br /><br /> [サーバー構成オプション &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)|  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] は、サポートされているすべてのデータベース互換性レベルで動作します。  
  
###  <a name="RestrictionsDb"></a> 制限事項 (可用性データベース)  
  
-   セカンダリ データベースのファイル パス (ドライブ文字を含む) が、対応するプライマリ データベースのパスと異なる場合、次の制限が適用されます。  
  
    -   **[!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]/[!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)]:**  **[完全]** オプションはサポートされません ([[最初のデータの同期を選択]](../../../database-engine/availability-groups/windows/select-initial-data-synchronization-page-always-on-availability-group-wizards.md) ページ)、  
  
    -   **RESTORE WITH MOVE:**  セカンダリ データベースを作成するには、セカンダリ レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の各インスタンス上で、WITH MOVE を使用してデータベース ファイルを復元する必要があります。  
  
    -   **ファイルの追加操作への影響:**  後でファイルの追加操作をプライマリ レプリカで実行した場合、セカンダリ データベースでエラーが発生する可能性があります。 この操作の失敗によってセカンダリ データベースが中断する可能性があります。 セカンダリ データベースが中断すると、セカンダリ レプリカが "NOT SYNCHRONIZING" 状態になります。  
  
        > [!NOTE]  
        >  ファイルの追加操作が失敗した場合の対処については、「[失敗したファイルの追加操作のトラブルシューティング &#40;Always On 可用性グループ&#41;](../../../database-engine/availability-groups/windows/troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)」を参照してください。  
  
-   可用性グループに現在属しているデータベースを削除することはできません。  
  
###  <a name="TDEdbs"></a> TDE で保護されたデータベースの補足情報  
 透過的なデータ暗号化 (TDE) を使用する場合、他のキーの作成および暗号化解除を行うための証明書または非対称キーは、可用性グループの可用性レプリカをホストするすべてのサーバー インスタンスで同じである必要があります。 詳細については、「 [別の SQL Server への TDE で保護されたデータベースの移動](../../../relational-databases/security/encryption/move-a-tde-protected-database-to-another-sql-server.md)」を参照してください。  
  
###  <a name="PermissionsDbs"></a> 権限 (可用性データベース)  
 データベースに対する ALTER 権限が必要です。  
  
###  <a name="RelatedTasksADb"></a> 関連タスク (可用性データベース)  
  
|タスク|トピック|  
|----------|-----------|  
|セカンダリ データベースの準備 (手動)|[可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)|  
|可用性グループへのセカンダリ データベースの参加 (手動)|[可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)|  
|可用性データベースの数の変更|[可用性グループへのデータベースの追加 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/availability-group-add-a-database.md)<br /><br /> [可用性グループからのセカンダリ データベースの削除 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-a-secondary-database-from-an-availability-group-sql-server.md)<br /><br /> [可用性グループからのプライマリ データベースの削除 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md)|  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   [高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [SQL Server Always On チームのブログ: SQL Server Always On チームのオフィシャル ブログ](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
-   [AlwaysOn - HADRON 学習シリーズ: HADRON 対応データベースのワーカー プールの使用](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [フェールオーバー クラスタリングと Always On 可用性グループ &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Always On クライアント接続 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-client-connectivity-sql-server.md)  
  
    
  
--------------------------------------------------  

