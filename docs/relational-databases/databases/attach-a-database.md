---
title: "データベースのインポート | Microsoft Docs"
ms.custom: 
ms.date: 10/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 04d101550bb7a1215c261419e42820af45ab5098
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="attach-a-database"></a>データベースのインポート
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のデータベースをアタッチする方法について説明します。 この機能は、SQL Server データベースのコピー、移動、またはアップグレードに使用できます。  
  
 
  
##  <a name="Prerequisites"></a> 前提条件  
  
-   最初にデータベースをデタッチする必要があります。 デタッチされていないデータベースをアタッチしようとすると、エラーが返されます。 詳細については、「 [データベースのデタッチ](../../relational-databases/databases/detach-a-database.md)」を参照してください。  
  
-   データベースをアタッチするときは、すべてのデータ ファイル (MDF ファイルおよび LDF ファイル) を利用できる状態にする必要があります。 データベースを最初に作成したときか最後にアタッチしたときとデータ ファイルのパスが異なる場合、ファイルの現在のパスを指定する必要があります。  
  
-   データベースをアタッチするときに、MDF ファイルと LDF ファイルが異なるディレクトリに配置されており、いずれかのパスに \\\\?\GlobalRoot が含まれている場合は、操作は失敗します。  
  
###  <a name="Recommendations"></a> アタッチの使用に適した状況  
 同一インスタンス内でデータベース ファイルを移動する場合は、デタッチ/アタッチではなく ALTER DATABASE による計画的な再配置手順でデータベースを移動することをお勧めします。 詳細については、「 [ユーザー データベースの移動](../../relational-databases/databases/move-user-databases.md)」を参照してください。 
 
バックアップおよび回復でのデタッチとアタッチの使用は推奨されません。 トランザクション ログのバックアップが存在しないだけでなく、ファイルが誤って削除される可能性があります。
  
###  <a name="Security"></a> セキュリティ  
 ファイル アクセス許可は、データベースのデタッチやアタッチなど、さまざまなデータベース操作中に設定されます。 データベースのデタッチおよびアタッチ時に設定されるファイル アクセス許可の詳細については、 [オンライン ブックの「](http://technet.microsoft.com/library/ms189128.aspx) データ ファイルとログ ファイルのセキュリティ保護 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 」を参照してください。この記事は旧バージョンを対象としたものですが、本バージョンにも有効です。 
  
 不明なソースや信頼されていないソースからデータベースをアタッチまたは復元しないことをお勧めします。 こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。 不明または信頼できないソースのデータベースを使用する前に、運用サーバー以外のサーバーでそのデータベースに対し [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。 データベースのアタッチ、およびデータベースのアタッチ時にメタデータに対して行われる変更の詳細については、「 [データベースのデタッチとアタッチ (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)」を参照してください。  
  
####  <a name="Permissions"></a> Permissions  
 CREATE DATABASE、CREATE ANY DATABASE、または ALTER ANY DATABASE の各権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-attach-a-database"></a>データベースをアタッチするには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーで [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続して、SSMS でそのインスタンスのビューを展開します。  
  
2.  **[データベース]** を右クリックし、 **[アタッチ]**をクリックします。  
  
3.  アタッチするデータベースを指定するには、 **[データベースのインポート]** ダイアログ ボックスで **[追加]**をクリックし、 **[データベース ファイルの検索]** ダイアログ ボックスで目的のデータベースが常駐するディスク ドライブを選択します。次に、そのディレクトリ ツリーを展開し、そのデータベースの .mdf ファイルを選択します。たとえば、次のように指定します。  
  
     `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    >  既にアタッチされているデータベースを選択しようとすると、エラーが発生します。  
  
     **[アタッチするデータベース]**  
     選択されたデータベースに関する情報を表示します。  
  
     \<空白の列ヘッダー>  
     アタッチ操作の状態を示すアイコンが表示されます。 表示されるアイコンの種類は、下の **[状態]** の説明に示します。  
  
     **[MDF ファイルの場所]**  
     選択した MDF ファイルのパスとファイル名が表示されます。  
  
     **Database Name**  
     データベースの名前が表示されます。  
  
     **[次の名前でアタッチ]**  
     データベースを別の名前でアタッチする場合に、その名前を指定します。  
  
     **[所有者]**  
     データベースの所有者のドロップダウン リストです。これを使用して、必要に応じて別の所有者を選択できます。  
  
     **ステータス**  
     次の表に示すように、データベースの状態を表示します。  
  
    |アイコン|状態テキスト|Description|  
    |----------|-----------------|-----------------|  
    |(アイコンなし)|(テキストなし)|このオブジェクトのアタッチ操作が開始されていないか、保留されています。 これは、ダイアログ ボックスを開いたときの既定の状態です。|  
    |緑の右向き三角形|[実行中]|アタッチ操作が開始されましたが、完了していません。|  
    |緑のチェック マーク|成功|オブジェクトは正常にアタッチされました。|  
    |赤い丸の中に白い×印|[エラー]|アタッチ操作でエラーが発生し、正常に完了しませんでした。|  
    |4 つに区切られた丸印 (左右の領域が黒、上下の領域が白)|停止|ユーザーがアタッチ操作を停止したため、正常に完了しませんでした。|  
    |丸の中に反時計回りの矢印|[ロールバックされました]|アタッチ操作は正常に完了しましたが、他のオブジェクトのアタッチ中にエラーが発生したため、ロールバックされました。|  
  
     **メッセージ**  
     空白のメッセージ、または "ファイルが見つかりません" のハイパーリンクが表示されます。  
  
     **[追加]**  
     主な必須データベース ファイルを検索します。 ユーザーが .mdf ファイルを選択した場合、 **[アタッチするデータベース]** グリッドの対応するフィールドに、対応する情報が自動的に入力されます。  
  
     **[削除]**  
     選択したファイルを **[アタッチするデータベース]** グリッドから削除します。  
  
     **"** *<database_name>* **" データベースの詳細**  
     デタッチするファイルの名前を表示します。 ファイルのパス名を確認または変更するには、 **参照** ボタン (**[...]**) をクリックしてください。  
  
    > [!NOTE]  
    >  ファイルが存在しなかった場合、 **[メッセージ]** 列に "見つかりませんでした" と表示されます。 ログ ファイルが見つからない場合は、ログ ファイルが別のディレクトリに置かれているか、削除されています。 **[データベースの詳細]** グリッドでファイル パスを更新し、正しい場所を指定するか、そのログ ファイルをグリッドから削除します。 .ndf データ ファイルが見つからない場合、グリッドのパスを更新して、正しい場所を指定する必要があります。  
  
     **[元のファイル名]**  
     データベースに属している、アタッチされたファイルの名前が表示されます。  
  
     **[ファイルの種類]**  
     ファイルの種類を表します。 **[データ]** または **[ログ]**になります。  
  
     **[現在のファイル パス]**  
     選択されているデータベース ファイルのパスを表示します。 このパスは手作業で編集できます。  
  
     **メッセージ**  
     空白のメッセージ、または**"ファイルが見つかりません"**ハイパーリンクが表示されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-attach-a-database"></a>データベースをアタッチするには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  FOR ATTACH 句を含む [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) ステートメントを使用します。  
  
     次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースのファイルをアタッチし、データベースの名前を `MyAdventureWorks`に変更します。  
  
    ```  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
  
    ```  
  
    > [!NOTE]  
    >  また、 [sp_attach_db](../../relational-databases/system-stored-procedures/sp-attach-db-transact-sql.md) ストアド プロシージャまたは [sp_attach_single_file_db](../../relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql.md) ストアド プロシージャを使用することもできます。 ただし、これらのプロシージャは、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の今後のバージョンでは削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、CREATE DATABASE … FOR ATTACH を使用することをお勧めします  
  
##  <a name="FollowUp"></a> 補足情報: SQL Server データベースのアップグレード後  
 アタッチする方法によってデータベースをアップグレードした後は、データベースが直ちに使用可能となり、自動的にアップグレードされます。 データベースにフルテキスト インデックスがある場合、アップグレード プロセスでは、 **[フルテキストのアップグレード オプション]** サーバー プロパティの設定に応じて、インポート、リセット、または再構築が行われます。 アップグレード オプションが **[インポート]** または **[再構築]**に設定されている場合、アップグレード中はフルテキスト インデックスを使用できなくなります。 インデックスを作成するデータ量によって、インポートには数時間、再構築には最大でその 10 倍の時間がかかることがあります。 なお、アップグレード オプションが **[インポート]**に設定されており、フルテキスト カタログが使用できない場合は、関連付けられたフルテキスト インデックスが再構築されます。  
  
 アップグレード前のユーザー データベースの互換性レベルが 100 以上の場合は、アップグレード後も互換性レベルは変わりません。 アップグレード前の互換性レベルが 90 の場合、アップグレードされたデータベースの互換性レベルは 100 に設定されます。これは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でサポートされている下限の互換性レベルです。 詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」を参照してください。  
  
  > [!NOTE]
  > Change Data Capture (CDC) が有効な SQL Server 2014 以下を実行するインスタンスからデータベースをアタッチする場合は、次のコマンドを実行して Change Data Capture (CDC) メタデータをアップグレードする必要もあります。
  ```
  USE <database name>
  EXEC sys.sp_cdc_vupgrade  
  ``` 
  
## <a name="see-also"></a>参照  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [データベースのデタッチ](../../relational-databases/databases/detach-a-database.md)  
  
  
