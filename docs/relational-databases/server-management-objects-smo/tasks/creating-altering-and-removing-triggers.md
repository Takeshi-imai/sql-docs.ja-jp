---
title: "作成、変更、およびトリガーの削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- triggers [SMO]
ms.assetid: 8ddbe23b-6e31-4f8e-8a70-17bd5072413e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fc1849a9bd38af6cbca6d9ebcbea6a571af8816c
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="creating-altering-and-removing-triggers"></a>トリガーの作成、変更、および削除
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]SMO では、トリガーを使用して表される、<xref:Microsoft.SqlServer.Management.Smo.Trigger>オブジェクト。 [!INCLUDE[tsql](../../../includes/tsql-md.md)]起動されたトリガーが設定されている場合に実行されるコード、<xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A>トリガー オブジェクトのプロパティです。 トリガーの型は、<xref:Microsoft.SqlServer.Management.Smo.Trigger> プロパティなど、<xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A> オブジェクトのその他のプロパティを使用することで設定します。 これはトリガーを起動するかどうかを指定するブール型プロパティ、**更新**親テーブルにレコードのです。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Trigger> オブジェクトは、従来のデータ操作言語 (DML) トリガーを表します。 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以降のバージョンでは、データ定義言語 (DDL) トリガーもサポートされます。 DDL トリガーは、<xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> オブジェクトおよび <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger> オブジェクトで表現します。  
  
## <a name="example"></a>例  
提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください[Visual C &#35; を作成する。Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  
 
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-basic"></a>Visual Basic でのトリガーの作成、変更、および削除  
 このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースにある `Sales` という名前の既存のテーブル上に、更新トリガーを作成および挿入する方法を示します。 トリガーによって、テーブルの更新時、または新規レコードの挿入時に通知メッセージが送信されます。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim mysrv As Server
mysrv = New Server
'Reference the AdventureWorks2012 2008R2 database.
Dim mydb As Database
mydb = mysrv.Databases("AdventureWorks2012")
'Declare a Table object variable and reference the Customer table.
Dim mytab As Table
mytab = mydb.Tables("Customer", "Sales")
'Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.
Dim tr As Trigger
tr = New Trigger(mytab, "Sales")
'Set TextMode property to False, then set other properties to define the trigger.
tr.TextMode = False
tr.Insert = True
tr.Update = True
tr.InsertOrder = Agent.ActivationOrder.First
Dim stmt As String
stmt = " RAISERROR('Notify Customer Relations',16,10) "
tr.TextBody = stmt
tr.ImplementationType = ImplementationType.TransactSql
'Create the trigger on the instance of SQL Server.
tr.Create()
'Remove the trigger.
tr.Drop()
``` 
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-c"></a>Visual C# でのトリガーの作成、変更、および削除  
 このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースにある `Sales` という名前の既存のテーブル上に、更新トリガーを作成および挿入する方法を示します。 トリガーによって、テーブルの更新時、または新規レコードの挿入時に通知メッセージが送信されます。  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            Server mysrv;  
            mysrv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database mydb;  
            mydb = mysrv.Databases["AdventureWorks2012"];  
            //Declare a Table object variable and reference the Customer table.   
            Table mytab;  
            mytab = mydb.Tables["Customer", "Sales"];  
            //Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.   
            Trigger tr;  
            tr = new Trigger(mytab, "Sales");  
            //Set TextMode property to False, then set other properties to define the trigger.   
            tr.TextMode = false;  
            tr.Insert = true;  
            tr.Update = true;  
            tr.InsertOrder = ActivationOrder.First;  
            string stmt;  
            stmt = " RAISERROR('Notify Customer Relations',16,10) ";  
            tr.TextBody = stmt;  
            tr.ImplementationType = ImplementationType.TransactSql;  
            //Create the trigger on the instance of SQL Server.   
            tr.Create();  
            //Remove the trigger.   
            tr.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-trigger-in-powershell"></a>PowerShell でのトリガーの作成、変更、および削除  
 このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースにある `Sales` という名前の既存のテーブル上に、更新トリガーを作成および挿入する方法を示します。 トリガーによって、テーブルの更新時、または新規レコードの挿入時に通知メッセージが送信されます。  
  
```powershell  
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the trigger's target table  
$mytab = get-item Sales.Customer  
  
# Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.  
$tr  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Trigger `  
-argumentlist $mytab, "Sales"  
  
# Set TextMode property to False, then set other properties to define the trigger.   
$tr.TextMode = $false  
$tr.Insert = $true  
$tr.Update = $true  
$tr.InsertOrder = [Microsoft.SqlServer.Management.SMO.Agent.ActivationOrder]::First  
$tr.TextBody = " RAISERROR('Notify Customer Relations',16,10) "  
$tr.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Create the trigger on the instance of SQL Server.   
$tr.Create()  
  
#Remove the trigger.   
$tr.Drop()  
```  
  
  
