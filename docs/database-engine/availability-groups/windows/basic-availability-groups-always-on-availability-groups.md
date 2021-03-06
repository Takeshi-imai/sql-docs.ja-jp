---
title: "基本的な可用性グループ (Always On 可用性グループ) | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 285adbc7-ac9b-40f6-b4a9-3f1591d3b632
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ba38095f11a5f40ec6b9a9398217a98f390d146d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="basic-availability-groups-always-on-availability-groups"></a>基本的な可用性グループ (AlwaysOn 可用性グループ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  基本的な AlwaysOn 可用性グループでは、SQL Server 2016 Standard Edition および SQL Server 2017 Standard Edition 用の高可用性ソリューションが提供されます。 基本的な可用性グループでは、単一のデータベースのフェールオーバー環境がサポートされます。 Enterprise Edition での従来の (拡張) [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) の場合と同じように作成され、管理されます。 このドキュメントでは、基本的な可用性グループの違いと制限の概要を示します。  
  
## <a name="features"></a>[機能]  
 基本的な AlwaysOn 可用性グループは、非推奨のデータベース ミラーリング機能に代わるものであり、同じようなレベルの機能サポートを提供します。 基本的な可用性グループを使用することで、プライマリ データベースは単一のレプリカを管理できます。 このレプリカでは同期コミット モードまたは非同期コミット モードを使用できます。 可用性モードの詳細については、「[可用性モード (AlwaysOn 可用性グループ)](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md)」をご覧ください。 セカンダリ レプリカは、フェールオーバーが必要にならない限り、非アクティブのままです。 このフェールオーバーでプライマリとセカンダリのロール割り当てが逆になり、セカンダリ レプリカがプライマリ アクティブ データベースになります。 フェールオーバーの詳細については、「[フェールオーバーとフェールオーバー モード &#40;AlwaysOn 可用性グループ&#41;](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)」をご覧ください。 基本的な可用性グループは、オンプレミスの環境と Microsoft Azure にまたがるハイブリッド環境で使用できます。  
  
## <a name="limitations"></a>制限事項  
 基本的な可用性グループでは、SQL Server 2016 Enterprise Edition の拡張可用性グループとは異なり、機能の一部のみを使用します。 基本的な可用性グループには以下の制限があります。  
  
- 使用できるレプリカは 2 つ (プライマリとセカンダリ) までです。  
  
- セカンダリ レプリカに対する読み取りアクセス権はありません。  
  
- セカンダリ レプリカではバックアップできません。  

- セカンダリ レプリカに対する整合性チェックはありません。 

- SQL Server 2016 Community Technology Preview 3 (CTP3) より前のバージョンの SQL Server を実行するサーバーでホストされるレプリカはサポートされません。  

- 可用性データベースは 1 つしかサポートされません。  
  
- 基本的な可用性グループを拡張可用性グループにアップグレードすることはできません。 グループを削除し、SQL Server 2016 Enterprise Edition のみを実行するサーバーを含むグループに再度追加する必要があります。  
  
- 基本的な可用性グループがサポートされるのは Standard Edition サーバーの場合のみです。 

- 基本的な可用性グループを分散型可用性グループの一部にすることはできません。 
  
## <a name="configuration"></a>構成  
 基本的な AlwaysOn 可用性グループは、2 つの SQL Server 2016 Standard Edition サーバーで作成できます。 基本的な可用性グループを作成する場合、作成時に両方のレプリカを指定する必要があります。  
  
 基本的な可用性グループを作成するには、**CREATE AVAILABILITY GROUP** という Transact-SQL コマンドを使用して、**WITH BASIC** (既定値は **ADVANCED**) オプションを指定します。 詳細については、「[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md)」を参照してください。 現時点では、SQL Server Management Studio で基本的な可用性グループを作成するための UI はサポートされていません。  
  
> [!NOTE]  
>  基本的な可用性グループの制限は、 **WITH BASIC** を指定した **CREATE AVAILABILITY GROUP** に適用されます。 たとえば、読み取りアクセスを許可する基本的な可用性グループを作成しようとすると、エラーが発生します。 他の制限も同様に適用されます。 詳細については、このトピックの「制限事項」を参照してください。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
