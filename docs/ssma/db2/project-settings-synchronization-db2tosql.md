---
title: "プロジェクトの Settings(Synchronization) (DB2ToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-db2
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: a5629a72-8c17-46a4-bb4d-19d51a0b98a2
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a701544d5f7d111d234b4a87def52beb3e1edbd
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="project-settingssynchronization-db2tosql"></a>プロジェクト Settings(Synchronization) (DB2ToSQL)
[同期] ページ、**プロジェクト設定** ダイアログ ボックスには、SSMA を読み込みますおよびにデータベース テーブルおよびストアド プロシージャなどのオブジェクトの更新方法をカスタマイズする設定が含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
既定のアクションのオプションは、DB2 データベースからオブジェクトを更新する場合と、SQL Server データベースとオブジェクトを同期するために、既定の設定を指定します。 詳細については、次を参照してください。[更新からのデータベース &#40;DB2ToSQL&#41;](../../ssma/db2/refresh-from-database-db2tosql.md)です。  
  
同じ設定を含む 2 つの異なる同期ページにアクセスできます。  
  
-   今後のすべての SSMA プロジェクトの設定を指定する、**ツール** メニューのをクリックして**プロジェクト設定の既定の**、クリックして**同期**左側のウィンドウの下部にあります。  
  
-   現在のプロジェクトの設定を指定する、**ツール** メニューのをクリックして**プロジェクト設定**、クリックして**同期**左側のウィンドウの下部にあります。  
  
## <a name="miscellaneous-options"></a>その他のオプション  
**試行回数**  
SSMA にオブジェクトの読み込み時に行う必要がありますの試行回数を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 オブジェクトに読み込まれていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]現在試行中に再試行されます SSMA が現在の同期プロセスの最大回数に達するまでします。 既定値のセットは**2**  
  
## <a name="synchronization-for-db2-options"></a>DB2 オプションの同期  
**ローカルおよびリモート オブジェクトの変更のアクション**  
SSMA では、データベース サーバーで、オブジェクトの定義が変更されたときに、[同期] ダイアログ ボックスで、既定の設定を指定します。 既定値のセットは**データベースから更新**です。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
**ローカル オブジェクトの変更のアクション**  
SSMA でオブジェクトが変更されたときに、[同期] ダイアログ ボックスで、既定の設定を指定します。 既定値のセットは**Skip**です。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
**リモート オブジェクトの変更のアクション**  
データベース サーバーで、オブジェクトが変更の同期 ダイアログ ボックスで、既定の設定を指定します。 既定値のセットは**データベースから更新**です。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
**ローカル オブジェクトのメタデータが不足している場合の動作**  
ローカルのメタデータが見つからない場合に、[同期] ダイアログ ボックスで、既定の設定を指定します。 既定値のセットは**データベースから更新**です。  
  
-   選択した場合**データベースから更新**、SSMA SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
## <a name="synchronization-for-sql-server-options"></a>SQL Server のオプションの同期  
**ローカルおよびリモート オブジェクトの変更のアクション**  
SSMA では、データベース サーバーで、オブジェクトの定義が変更されたときに、[同期] ダイアログ ボックスで、既定の設定を指定します。 既定値のセットは**データベースへの書き込み**です。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、SSMA メタデータの内容に基づき、データベース内のオブジェクトは更新します。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
**ローカル オブジェクトの変更のアクション**  
SSMA でオブジェクトが変更されたときに、[同期] ダイアログ ボックスで、既定の設定を指定します。 既定値のセットは**データベースへの書き込み**です。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、SSMA メタデータの内容に基づき、データベース内のオブジェクトは更新します。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
**リモート オブジェクトの変更のアクション**  
データベース サーバーで、オブジェクトが変更の同期 ダイアログ ボックスで、既定の設定を指定します。  既定値のセットは**データベースから更新**です。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、SSMA メタデータの内容に基づき、データベース内のオブジェクトは更新します。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
**ローカル オブジェクトのメタデータが不足している場合の動作**  
ローカルのメタデータが見つからない場合に、[同期] ダイアログ ボックスで、既定の設定を指定します。 既定値のセットは**データベースから更新**です。  
  
-   選択した場合**データベースから更新**、SSMA を選択、**データベースから更新**オプション条件が満たされたときにします。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、データベースからのオブジェクトが削除されます。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
