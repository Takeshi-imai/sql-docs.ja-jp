---
title: "DDL トリガーに関する情報の取得 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: triggers
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-ddl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metadata [SQL Server], triggers
- status information [SQL Server], DDL triggers
- DDL triggers, metadata
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ae01a87b0697165fe9ed66d80645f87fc8a5f19
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="get-information-about-ddl-triggers"></a>DDL トリガーに関する情報の取得
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
ここに記載されているカタログ ビューを使用すると、DDL トリガーに関する情報を取得できます。  
  
 **DDL トリガーを起動できるイベントまたはイベント グループに関する情報を取得するには**  
  
-   [sys.trigger_event_types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql.md)  
  
 **トリガーの依存関係を表示するには**  
  
-   [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
-   [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)  
  
-   [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)  
  
## <a name="database-scoped-ddl-triggers"></a>データベース スコープの DDL トリガー  
 **データベース スコープのトリガーに関する情報を取得するには**  
  
-   [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)  
  
 **トリガーを起動するデータベース イベントに関する情報を取得するには**  
  
-   [sys.trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)  
  
 **データベース スコープのトリガーの定義を表示するには**  
  
-   [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)  
  
 **データベース スコープの CLR トリガーに関する情報を取得するには**  
  
-   [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)  
  
## <a name="server-scoped-ddl-triggers"></a>サーバー スコープの DDL トリガー  
 **サーバー スコープのトリガーに関する情報を取得するには**  
  
-   [sys.server_triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)  
  
 **トリガーを起動するサーバー イベントに関する情報を取得するには**  
  
-   [sys.server_trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)  
  
 **サーバー スコープのトリガーの定義を表示するには**  
  
-   [sys.server_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)  
  
 **サーバー スコープの CLR トリガーに関する情報を取得するには**  
  
-   [sys.server_assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
## <a name="see-also"></a>参照  
 [DDL トリガー](../../relational-databases/triggers/ddl-triggers.md)  
  
  
