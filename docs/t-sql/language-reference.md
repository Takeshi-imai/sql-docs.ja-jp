---
title: "Transact-SQL リファレンス (データベース エンジン) | Microsoft Docs"
ms.custom: 
ms.date: 04/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sql13.tsqlref.f1
- devlang-tsql
helpviewer_keywords:
- Transact-SQL
ms.assetid: dbba47d7-e08e-4435-b876-35dced1f325d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 9bc588f23d4a78d035a46c7e5c1adcb600af1ce2
ms.sourcegitcommit: aebbfe029badadfd18c46d5cd6456ea861a4e86d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
---
# <a name="transact-sql-reference-database-engine"></a>Transact-SQL リファレンス (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]

このトピックでは、Microsoft Transact-SQL (T-SQL) のリファレンス トピックを見つけて使用する方法の基本事項を説明します。 T-SQL は、Microsoft SQL の製品やサービスを使用するときの中心となる機能です。 SQL データベースと通信するツールやアプリケーションはすべて、T-SQL のコマンドを送信するという方法で通信します。  

## <a name="tools-that-use-t-sql"></a>T-SQL を使用するツール

Microsoft のツールのうち、T-SQL のコマンドを発行する主なものは次のとおりです。

- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)
- [SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md)  
- [sqlcmd](../tools/sqlcmd-utility.md)  
- [SQL Operations Studio (プレビュー)](https://docs.microsoft.com/sql/sql-operations-studio/download)  
  
 
## <a name="locate-the-transact-sql-reference-topics"></a>Transact-SQL のリファレンス トピックを見つける  
  
T-SQL のトピックを見つけるには、このページの右上にある検索ボックスを使用するか、ページの左側にある目次を使用します。 また、T-SQL のキーワードを Management Studio のクエリ エディター ウィンドウで入力して F1 キーを押すという方法もあります。 
  

## <a name="find-system-views"></a>システム ビューを見つける

システム テーブル、ビュー、関数、プロシージャを見つけるには、下記のリンクを参照してください。これらは、SQL のドキュメントの[リレーショナル データベースの使用](../relational-databases/database-features.md)のセクションにあります。

- [システム カタログ ビュー](../relational-databases/system-catalog-views/catalog-views-transact-sql.md)
- [システム互換性ビュー](../relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)
- [システム動的管理ビュー](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
- [システム関数](../relational-databases/system-functions/system-functions-for-transact-sql.md)
- [システム情報スキーマ ビュー](../relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)
- [システム ストアド プロシージャ](../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)
- [システム テーブル](../relational-databases/system-tables/system-tables-transact-sql.md)

 
## <a name="applies-to-references"></a>"適用されます" リファレンス  
 T-SQL のリファレンス トピックは、SQL Server 2008 以降の複数のバージョンを対象としており、その他に Azure SQL のサービスも対象としています。 各トピックの先頭近くにあるセクションで、どの製品やサービスがそのトピックの説明対象をサポートしているかを示しています。 

たとえば、このトピックはすべてのバージョンに適用されるため、次のようなラベルが付いています。 
  
 [!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]   

次の例のラベルは、トピックが Azure SQL Data Warehouse と Parallel Data Warehouse だけに適用されることを示しています。

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  
場合によっては、トピックがある製品またはサービスで使用されていても、引数のすべてがサポートされているわけではないこともあります。 この場合は、別の "**適用されます**" セクションが、そのトピック本文中の該当する引数の説明の中に挿入されます。  
 
## <a name="get-help-from-the-msdn-forum"></a>MSDN フォーラムで支援を受ける  
  
オンラインで支援を受けるには、[MSDN Transact-SQL フォーラム](http://social.msdn.microsoft.com/Forums/en-US/home?forum=transactsql)を参照してください。  
 
## <a name="see-other-language-references"></a>その他の言語リファレンス

SQL のドキュメントには、他にも次のような言語リファレンスが含まれています。
  
- [XQuery 言語リファレンス](../xquery/xquery-language-reference-sql-server.md)
- [Integration Services 言語リファレンス](../integration-services/integration-services-language-reference.md)
- [レプリケーション言語リファレンス](../relational-databases/replication/replication-language-reference.md)
- [Analysis Services 言語リファレンス](../mdx/analysis-services-language-reference.md)  


## <a name="next-steps"></a>次の手順

T-SQL のリファレンス トピックを見つける方法を理解したので、次のことができるようになりました。

- T-SQL を書く方法を短いチュートリアルで学習します。「[チュートリアル: Transact-SQL ステートメントの作成](../t-sql/tutorial-writing-transact-sql-statements.md)」を参照してください。 
- 「[Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)」を参照します。  

  
  
