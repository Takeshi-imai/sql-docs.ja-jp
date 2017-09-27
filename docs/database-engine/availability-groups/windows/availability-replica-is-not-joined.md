---
title: "可用性レプリカが参加していない | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.agdashboard.arp4joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 9c0d10b1-9e12-430c-83b9-ca2bd0a3afc4
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 84fda9d15b375773c02029c68c7517201fb51a1d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="availability-replica-is-not-joined"></a>可用性レプリカが参加していない
    
## <a name="introduction"></a>概要  
  
|||  
|-|-|  
|**ポリシー名**|可用性レプリカの参加状態|  
|**問題点**|可用性レプリカが参加していません。|  
|**カテゴリ**|**警告**|  
|**ファセット**|可用性レプリカ|  
  
## <a name="description"></a>説明  
 このポリシーは、可用性レプリカの参加状態をチェックします。 可用性レプリカが可用性グループに追加されていても、適切に参加していない場合、ポリシーは異常な状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [Availability Replica Is not joined (可用性レプリカが参加していない)](http://go.microsoft.com/fwlink/p/?LinkId=220859) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## <a name="possible-causes"></a>考えられる原因  
 セカンダリ レプリカが可用性グループに参加していません。 可用性レプリカを可用性グループに正しく参加させるには、参加状態が Joined Standalone Instance (1) または Joined Failover Cluster (2) である必要があります。  
  
## <a name="possible-solution"></a>考えられる解決方法  
 Transact-SQL、PowerShell、または SQL Server Management Studio を使用して、セカンダリ レプリカを可用性グループに参加させます。 セカンダリ レプリカを可用性グループに参加させる方法の詳細については、「 [可用性グループへのセカンダリ レプリカの参加 (SQL Server)](http://msdn.microsoft.com/library/ff878473\(SQL.110\).aspx)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
