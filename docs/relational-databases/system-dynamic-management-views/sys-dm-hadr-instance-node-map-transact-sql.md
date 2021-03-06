---
title: sys.dm_hadr_instance_node_map (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sys.dm_hadr_instance_node_map_TSQL
- sys.sys.dm_hadr_instance_node_map
- sys.dm_hadr_instance_node_map_TSQL
- sys.dm_hadr_instance_node_map
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.sys.dm_hadr_instance_node_map dynamic management view
ms.assetid: ccfaf62c-9f87-43cf-a5e7-8942e91dd041
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 61d86f7ac8fda6d975f9f0ff2fc9aaf58af55aa9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmhadrinstancenodemap-transact-sql"></a>sys.dm_hadr_instance_node_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  すべてのインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Always On 可用性グループに参加している、サーバー インスタンスをホストする Windows Server フェールオーバー クラスタ リング (WSFC) ノードの名前を取得する可用性レプリカをホストします。 この動的管理ビューには、次の用途があります。  
  
-   この動的管理ビューは、同一の WSFC ノードでホストされている複数の可用性レプリカを持つ可用性グループを検出するために役に立ちます。これはサポート外の構成であり、可用性グループが間違って構成されているときに FCI フェールオーバーが発生した場合にこの状態になることがあります。 詳細については、「[フェールオーバー クラスタリングと Always On 可用性グループ #40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)」を参照してください。  
  
-   インスタンスを指定するリソース DLL がこの動的管理ビューを使用して同一の WSFC ノードでは、複数の SQL Server インスタンスがホストされている、ときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続します。  
   
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**ag_resource_id**|**nvarchar (256)**|WSFC クラスターのリソースとしての可用性グループの一意な ID。|  
|**instance_name**|**nvarchar (256)**|名前:*サーバー*/*インスタンス*: 可用性グループのレプリカをホストするサーバー インスタンスのです。|  
|**node_name**|**nvarchar (256)**|WSFC クラスター ノードの名前。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [AlwaysOn 可用性グループのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [可用性グループの監視と &#40; です。Transact SQL と &#41; です。](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
