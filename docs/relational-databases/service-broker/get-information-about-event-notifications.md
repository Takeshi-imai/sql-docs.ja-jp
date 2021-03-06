---
title: "イベント通知に関する情報の取得 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: service-broker
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3e8a2f7837c7f18293afe66c168b5d52c8b03da9
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="get-information-about-event-notifications"></a>イベント通知に関する情報の取得
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
次のカタログ ビューは、イベント通知に関するメタデータのクエリに使用できます。  
  
 **サーバー以外のレベルのイベント通知に関する情報を取得するには**  
  
-   [sys.event_notifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  データベース レベルで作成した **sys.event_notifications** の任意のイベント通知に関するメタデータを表示するには、少なくとも、データベースに対して CONTROL 権限、ALTER 権限、TAKE OWNERSHIP 権限、または VIEW DEFINITION 権限を持っているか、イベント通知の所有者であるか、ALTER ANY DATABASE EVENT NOTIFICATION 権限を持っている必要があります。 特定のキューで作成したイベント通知の場合は、少なくとも、オブジェクトに対して CONTROL 権限、ALTER 権限、TAKE OWNERSHIP 権限、または VIEW DEFINITION 権限を持っているか、イベント通知の所有者であるか、ALTER ANY DATABASE EVENT NOTIFICATION 権限を持っている必要があります。  
  
 **サーバーレベルのイベント通知に関する情報を取得するには**  
  
-   [sys.server_event_notifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  **sys.server_event_notifications**の任意のイベント通知に関するメタデータを表示するには、少なくとも、サーバーに対して CONTROL 権限または VIEW ANY DEFINITION 権限を持っているか、イベント通知のログオンまたは所有者であるか、ALTER ANY EVENT NOTIFICATION 権限を持っている必要があります。  
  
 **イベント通知を発生させることができるすべてのイベントに関する情報を取得するには**  
  
-   [sys.event_notification_event_types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql.md)  
  
> [!NOTE]  
>  このカタログ ビューからイベント グループが返されることはありません。  
  
## <a name="see-also"></a>参照  
 [イベント通知](../../relational-databases/service-broker/event-notifications.md)  
  
  
