---
title: "データベース互換性モードの変更とクエリ ストアの使用 | Microsoft Docs"
ms.custom: 
ms.date: 07/21/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2701a951f0c8847b028e3a87717ad9ac3a965529
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="change-the-database-compatibility-mode-and-use-the-query-store"></a>データベース互換性モードの変更とクエリ ストアの使用

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、一部の変更は、[データベースの互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)が変更された後に有効になります。 これは、次の理由のためです。  
  
- アップグレードは一方向の操作である (ファイル形式をダウン グレードできない) ため、データベース内で新機能を有効にする操作を別の操作に分離することが重要です。 以前のデータベース互換性レベルに設定を戻すことができます。  新しいモデルでは、停止期間中に発生する処理の数が減ります。  
  
- クエリ プロセッサに対する変更は、複雑な影響をもたらす可能性があります。 システムに対する "良い" 変更は、ほとんどのワークロードには有益であっても、その他のワークロードにとって重要なクエリで許容できない回帰を引き起こす可能性があります。 アップグレード プロセスからこのロジックを分離すると、クエリ ストアなどの機能は、プラン選択の回帰を迅速に緩和し、さらには実稼働サーバーで完全に回避できます。  
  
> [!IMPORTANT]  
> アップグレード前のユーザー データベースの互換性レベルが 100 以上の場合は、アップグレード後も互換性レベルは変わりません。    
> アップグレード前のユーザー データベースの互換性レベルが 90 の場合、アップグレードされたデータベースの互換性レベルは 100 に設定されます。これは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でサポートされている下限の互換性レベルです。    
> tempdb、model、msdb、および Resource データベースの互換性レベルは、アップグレード後に現在の互換性レベルに設定されます。   
> master システム データベースは、アップグレード前の互換性レベルを保持します。    
  
新しいクエリ プロセッサの機能を有効にするためのアップグレード プロセスは、製品のリリース後のサービス モデルに関連付けられます。  それらの修正プログラムの一部は、[トレース フラグ 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md#4199) でリリースされます。  修正プログラムを必要とするユーザーは、他のユーザーにとって予期しない回帰を引き起こすことなくそれらの修正プログラムを適用できます。 クエリ プロセッサの修正プログラムのリリース後のサービス モデルは、 [ここ](http://support.microsoft.com/kb/974006)に記載されています。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降では、新しい互換性レベルに移行した場合、トレース フラグ 4199 は不要になります。これは、それらの修正プログラムは最新の互換レベルで既定で有効になっているためです。 そのため、アップグレード プロセスの一環として、アップグレード プロセスが完了したら、4199 が無効になっていることを検証することが重要です。  

> [!NOTE]
> ただし、RTM の後にリリースされた新しいクエリ プロセッサの修正プログラムを有効にするためには (該当する場合)、トレース フラグ 4199 が必要です。
  
以下のような、クエリ プロセッサを最新バージョンのコードにアップグレード場合に推奨されるワークフローについては、「[新しい SQL Server にアップグレードするときにパフォーマンスの安定性を維持する](../../relational-databases/performance/query-store-usage-scenarios.md#CEUpgrade)」を参照してください。  
  
![query-store-usage-5](../../relational-databases/performance/media/query-store-usage-5.png "query-store-usage-5") 
 
## <a name="see-also"></a>参照  
 [データベースの互換性レベルの表示または変更](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)  
 [クエリ ストアの使用シナリオ](../../relational-databases/performance/query-store-usage-scenarios.md) 
  
