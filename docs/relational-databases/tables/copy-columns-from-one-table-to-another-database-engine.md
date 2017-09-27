---
title: "テーブル間での列のコピー (データベース エンジン) | Microsoft Docs"
ms.custom: 
ms.date: 09/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- copying columns
- columns [SQL Server], copying
ms.assetid: 5f5e70dc-69f9-44b8-bc48-b5d51ac20d77
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 27f2f6ae3af99a9c76934ab4c875d3c2c9746f40
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="copy-columns-from-one-table-to-another-database-engine"></a>テーブル間での列のコピー (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]で列の定義のみ、または定義とデータの両方をコピーすることで、あるテーブルから別のテーブルに列をコピーする方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **列をコピーする方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 別名データ型の列をデータベース間でコピーする場合、コピー先のデータベースで同じ別名データ型を使用できない場合があります。 その場合、コピー先データベースで使用できる基本データ型の中で最も近いデータ型がその列に割り当てられます。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a>テーブル間で列の定義をコピーするには  
  
1.  コピーする列を含むテーブルおよびコピー先のテーブルを右クリックして **[デザイン]**をクリックし、それらのテーブルを開きます。  
  
2.  コピーする列を含むテーブルのタブをクリックして、コピーする列を選択します。  
  
3.  **[編集]** メニューの **[コピー]**をクリックします。  
  
4.  列をコピーする先のテーブルのタブをクリックします。  
  
5.  コピーした列を挿入する列を選択し、 **[編集]** メニューの **[貼り付け]**をクリックします。  
  
#### <a name="to-copy-data-from-one-table-to-another"></a>テーブル間でデータをコピーするには  
  
1.  前述の列定義のコピーの指示に従います。  
  
    > [!NOTE]  
    >  テーブル間でデータのコピーを始める前に、コピー先の列のデータ型が、コピー元の列のデータ型と互換性があることを確認してください。  
  
2.  新しいクエリ エディター ウィンドウを開きます。 

3.  クエリ エディターを右クリックし、 **[エディターでクエリをデザイン]**をクリックします。 

4.  **[テーブルの追加]** ダイアログ ボックスで、コピー元テーブルとコピー先テーブルを選択し、 **[追加]**をクリックして **[テーブルの追加]** ダイアログ ボックスを閉じます。 

5.  クエリ エディターの空いている領域を右クリックし、 **[変更の種類]**をポイントして **[結果の挿入]**をクリックします。  

6.  **[結果の挿入先テーブルの選択]** ダイアログ ボックスで、コピー先テーブルを選択します。 

7.  クエリ デザイナーの上部で、コピー元テーブル内のコピー元列をクリックします。

8. これで、クエリ デザイナーで INSERT クエリが作成されました。 [OK] をクリックして、クエリを元のクエリ エディター ウィンドウに配置します。  

9.  クエリを実行して、コピー元テーブルからコピー先テーブルにデータを挿入します。

  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a>テーブル間で列の定義をコピーするには  
  
1.  Transact-SQL ステートメントを使用して、個々の列をあるテーブルから別の既存のテーブルにコピーすることはできません。 ただし、SELECT INTO を使用して、既定のファイル グループに新しいテーブルを作成し、クエリの結果得られた行をそのテーブルに挿入することができます。 詳細については、「[INTO 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-into-clause-transact-sql.md)」を参照してください。  
  
#### <a name="to-copy-data-from-one-table-to-another"></a>テーブル間でデータをコピーするには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.EmployeeSales  
    ( BusinessEntityID   varchar(11) NOT NULL,  
      SalesYTD money NOT NULL  
    );  
    GO  
    INSERT INTO dbo.EmployeeSales  
        SELECT BusinessEntityID, SalesYTD   
        FROM Sales.SalesPerson;  
    GO  
    ```  
  
  
