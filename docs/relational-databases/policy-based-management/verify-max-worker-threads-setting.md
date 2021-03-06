---
title: "max worker threads 設定の検証 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b4d37255a42c0b219398f1ae23ba0687da22dc13
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="verify-max-worker-threads-setting"></a>max worker threads 設定の検証
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このルールでは、max worker threads サーバー オプションに不適切な設定がないかどうかを確認します。 max worker threads オプションに小さい値を設定すると、必要な数のスレッドを確保できなくて着信クライアント要求に適切なタイミングで対応できず、"スレッド不足" に陥る可能性があります。 その反面、アクティブな各スレッドは、64 ビット サーバー上で最大 4 MB を消費するので、このオプションを大きい値に設定すると、アドレス空間が無駄に使用される可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 max worker threads オプションを 0 に設定します。 この設定により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ユーザー要求に基づいてアクティブなワーカー スレッドの適切な数が自動的に決定されます。  
  
## <a name="for-more-information"></a>詳細情報  
 [max worker threads サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
