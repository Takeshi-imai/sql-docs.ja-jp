---
title: "システム バージョン管理されたテンポラル テーブルの概要 | Microsoft Docs"
ms.custom: 
ms.date: 03/28/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d431f216-82cf-4d97-825e-bb35d3d53a45
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 456602d6543527b1826dc21f93859f75629fd1a1
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="getting-started-with-system-versioned-temporal-tables"></a>システム バージョン管理されたテンポラル テーブルの概要
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  シナリオに応じて、システム バージョン管理された新しいテンポラル テーブルを作成するか、既存のテーブル スキーマにテンポラル属性を追加して既存のテーブルを変更できます。   
テンポラル テーブル内のデータが変更されると、バージョン履歴がアプリケーションとエンド ユーザーに対して透過的に構築されます。 このため、システム バージョン管理されたテンポラル テーブルの操作では、テーブルの変更方法や最新 (実際の) データへのクエリの実行方法を変更する必要はありません。   
また、テンポラルには、通常の DML やクエリ実行のほかに、拡張 Transact-SQL 構文でデータ履歴から情報を簡単かつ便利に取得する方法も用意されています。   
すべてのシステム バージョン管理されたテーブルに履歴テーブルが割り当てられていますが、これはユーザーに対して完全に透過的です。ただし、ユーザーが追加のインデックスを作成するか、別のストレージ オプションを選択して、ワークロードのパフォーマンスまたはストレージの使用量を最適化する必要がある場合は除きます。    
次の図は、システム バージョン管理されたテンポラル テーブルの一般的なワークフローを示しています。   
![テンポラルの概要](../../relational-databases/tables/media/getting-started-with-temporal.png "テンポラルの概要")  
  
 このトピックには、次の 5 つのセクションがあります。  
  
-   [システム バージョン管理されたテンポラル テーブルの作成](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)  
  
-   [システム バージョン管理のテンポラル テーブルのデータの変更](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)  
  
-   [システム バージョン管理されたテンポラル テーブルのデータのクエリ](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)  
  
-   [システム バージョン管理されたテンポラル テーブルのスキーマを変更する](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)  
  
-   [システム バージョン管理されたテンポラル テーブルでシステム バージョン管理を停止する](../../relational-databases/tables/stopping-system-versioning-on-a-system-versioned-temporal-table.md)  
  
## <a name="did-this-article-help-you-were-listening"></a>この記事は役に立ちましたか? フィードバックをお待ちしております。  
 どのような情報をお探しでしたか? お探しの情報は見つかりましたか? コンテンツ改善のため、フィードバックをお待ちしています。 [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Getting%20Started%20with%20System-Versioned%20Temporal%20Tables%20page) にコメントをお送りください  
  
## <a name="see-also"></a>参照  
 [テンポラル テーブル](../../relational-databases/tables/temporal-tables.md)   
 [テンポラル テーブルのシステム一貫性のチェック](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [テンポラル テーブルでのパーティション分割](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [テンポラル テーブルの考慮事項と制約](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [テンポラル テーブル セキュリティ](../../relational-databases/tables/temporal-table-security.md)   
 [システム バージョン管理されたテンポラル テーブルの履歴データの保有期間管理](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [メモリ最適化テーブルでのシステム バージョン管理されたテンポラル テーブル](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [テンポラル テーブル メタデータのビューおよび関数](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
