---
title: "主キーの削除 | Microsoft Docs"
ms.custom: 
ms.date: 07/25/2017
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
helpviewer_keywords:
- removing primary keys
- deleting primary keys
- primary keys [SQL Server], deleting
ms.assetid: c472e465-7bdd-4d74-8fc9-e47fca007ccb
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 185ab2d26ef049e211ae42624dae3e1517361cca
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="delete-primary-keys"></a>主キーの削除
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して主キーを削除できます。 主キーを削除すると、対応するインデックスが削除されます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **主キー制約を削除する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-delete-a-primary-key-constraint-using-object-explorer"></a>オブジェクト エクスプローラーを使用して主キーを削除するには  
  
1.  オブジェクト エクスプローラーで、主キーを含むテーブルを展開し、 **[キー]**を展開します。  
  
2.  キーを右クリックし、 **[削除]**をクリックします。  
  
3.  **[オブジェクトの削除]** ダイアログ ボックスで正しいキーが指定されていることを確認し、 **[OK]**をクリックします。  
  
#### <a name="to-delete-a-primary-key-constraint-using-table-designer"></a>テーブル デザイナーを使用して主キーを削除するには  
  
1.  オブジェクト エクスプローラーで、主キーが設定されたテーブルを右クリックし、 **[デザイン]**をクリックします。  
  
2.  テーブル グリッドで、主キーを持つ行を右クリックし、 **[主キーの削除]** をクリックして、設定をオンからオフに切り替えます。  
  
    > [!NOTE]  
    >  この操作を元に戻すには、変更を保存せずにテーブルを閉じます。 主キーの削除を元に戻すと、テーブルに対するその他の変更はすべて失われます。  
  
3.  **[ファイル]** メニューの *[<テーブル名> を保存]* をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-delete-a-primary-key-constraint"></a>主キー制約を削除するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 次の例では、まず主キー制約の名前を指定してから制約を削除します。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Return the name of primary key.  
    SELECT name  
    FROM sys.key_constraints  
    WHERE type = 'PK' AND OBJECT_NAME(parent_object_id) = N'TransactionHistoryArchive';  
    GO  
    -- Delete the primary key constraint.  
    ALTER TABLE Production.TransactionHistoryArchive  
    DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID;   
    GO  
    ```  
  
 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)」および「[sys.key_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)」を参照してください。  
  
###  <a name="TsqlExample"></a>  
