---
title: "SQL Server のフェールオーバー クラスター インスタンスの名前変更 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: failover-clusters
ms.prod_service: sql-non-specified
ms.service: database-engine
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clusters [SQL Server], virtual servers
- renaming virtual servers
- virtual servers [SQL Server], failover clustering
- failover clustering [SQL Server], virtual servers
ms.assetid: 2a49d417-25fb-4760-8ae5-5871bfb1e6f3
caps.latest.revision: "16"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9e57c999cd35129131f124aa6319b09b91ff99d9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="rename-a-sql-server-failover-cluster-instance"></a>SQL Server のフェールオーバー クラスター インスタンスの名前変更
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] フェールオーバー クラスターに含まれる [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの場合、仮想サーバーの名前を変更する手順は、スタンドアロン インスタンスでの手順とは異なります。 詳細については、 [SQL Server のスタンドアロン インスタンスをホストするコンピューターの名前変更](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)を参照してください。  
  
 仮想サーバーの名前は、常に SQL ネットワーク名 (SQL 仮想サーバー ネットワーク名) と同じになります。 仮想サーバー名は変更できますが、インスタンス名は変更できません。 たとえば、VS1\instance1 という仮想サーバー名を SQL35\instance1 などの別の名前に変更することはできますが、名前のインスタンスの部分 instance1 は変更されません。  
  
 名前の変更処理を開始する前に、次の項目を確認します。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、レプリケーションにログ配布が使用されている場合を除いて、レプリケーション対象サーバーの名前は変更できません。 プライマリ サーバーが完全に存在しなくなった場合は、ログ配布対象のセカンダリ サーバーの名前を変更することができます。 詳細については、[ログ配布とレプリケーション &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md) を参照してください。  
  
-   データベース ミラーリングを使用するよう構成されている仮想サーバーの名前を変更する場合は、名前の変更を行う前にデータベース ミラーリングを無効にし、名前の変更後に新しい仮想サーバー名でデータベース ミラーリングを再確立する必要があります。 データベース ミラーリングのメタデータは、新しい仮想サーバー名に、自動的には更新されません。  
  
### <a name="to-rename-a-virtual-server"></a>仮想サーバーの名前を変更するには  
  
1.  クラスター アドミニストレーターを使用して、SQL ネットワーク名を新しい名前に変更します。  
  
2.  ネットワーク名リソースをオフラインにします。 これにより、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースや、他の依存リソースもオフラインになります。  
  
3.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースをオンラインに戻します。  
  
## <a name="verify-the-renaming-operation"></a>名前の変更操作の確認  
 仮想サーバーの名前を変更したら、このサーバーの古い名前を使用している接続は、新しい名前を使用して接続するように変更する必要があります。  
  
 名前の変更が完了していることを確認するには、**@@servername** または **sys.servers** のいずれかを使用して情報を取得します。 **@@servername** 関数は新しい仮想サーバー名を返し、**sys.servers** テーブルには新しい仮想サーバー名が表示されます。 また、フェールオーバー処理が新しい名前を使って正常に機能していることを確認するには、他のノードに対する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースのフェールオーバーが発生するように試行します。  
  
 クラスター内のノードからの接続については、新しい名前を直ちに使用できます。 ただし、クライアント コンピューターから新しい名前を使用して接続する場合は、クライアント コンピューターが新しい名前を認識できるようにならないと、新しい名前を使用してサーバーに接続することはできません。 新しい名前がネットワーク全体に伝達されるのに必要な時間は、ネットワークの構成により異なり、数秒で済むことも、3 ～ 5 分かかることもあります。ネットワークから古い仮想サーバー名が消去されるには、さらに時間がかかる場合があります。  
  
 仮想サーバー名の変更をネットワークに伝達する時間を最小限に抑えるには、次の手順を実行します。  
  
#### <a name="to-minimize-network-propagation-delay"></a>ネットワークの伝達の遅延を最小限に抑えるには  
  
1.  サーバー ノードでコマンド プロンプトから次のコマンドを実行します。  
  
    ```  
    ipconfig /flushdns  
    ipconfig /registerdns  
    nbtstat –RR  
    ```  
  
## <a name="additional-considerations-after-the-renaming-operation"></a>名前変更操作後のその他の考慮事項  
 フェールオーバー クラスターのネットワーク名を変更した後は、以下の点を検証および実行して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントと [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のすべてのシナリオを有効にする必要があります。  
  
 **[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービス:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスに推奨される以下の追加事項を検証および実行します。  
  
-   SQL エージェントがイベントの転送用に構成されている場合は、レジストリ設定を修正します。 詳細については、[イベントの転送先サーバーの指定 &#40;SQL Server Management Studio&#41;](http://msdn.microsoft.com/library/81dfcbe4-3000-4e77-99de-bf85fef63a12) を参照してください。  
  
-   コンピューター/クラスターのネットワーク名が変更されている場合は、マスター サーバー (MSX) と対象サーバー (TSX) のインスタンス名を修正します。 詳細については、次の各トピックを参照してください。  
  
    -   [マスター サーバーからの複数の対象サーバーの参加の解除](http://msdn.microsoft.com/library/61a3713b-403a-4806-bfc4-66db72ca1156)  
  
    -   [マルチサーバー環境の作成](http://msdn.microsoft.com/library/edc2b60d-15da-40a1-8ba3-f1d473366ee6)  
  
-   ログ配布を再構成して、更新されたサーバー名を使ってログがバックアップおよび復元されるようにします。 詳細については、次の各トピックを参照してください。  
  
    -   [ログ配布の構成 &#40;SQL Server&#41;](../../../database-engine/log-shipping/configure-log-shipping-sql-server.md)  
  
    -   [ログ配布の削除 &#40;SQL Server&#41;](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
-   サーバー名を使用するジョブ ステップを更新します。 詳細については、 [ジョブ ステップの管理](http://msdn.microsoft.com/library/51352afc-a0a4-428b-8985-f9e58bb57c31)を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server のスタンドアロン インスタンスをホストするコンピューターの名前変更](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)  
  
  
