---
title: "sqlps ユーティリティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sqlps
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
caps.latest.revision: "22"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bd4e67397b52b3e7248ce061312517841eef38e5
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sqlps-utility"></a>sqlps ユーティリティ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]**Sqlps**ユーティリティは、Windows PowerShell セッションを起動し、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell プロバイダーおよびコマンドレットの読み込みし、登録します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell コンポーネントを使用する PowerShell コマンドやスクリプトを入力して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスとそのオブジェクトを操作できます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]使用して、 **sqlps** PowerShell モジュール代わりにします。 **sqlps** モジュールの詳細については、「 [Import the SQLPS Module](../relational-databases/scripting/import-the-sqlps-module.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlps   
[ [ [ -NoLogo ][ -NoExit ][ -NoProfile ]  
    [ -OutPutFormat { Text | XML } ] [ -InPutFormat { Text | XML } ]  
  ]  
  [ -Command { -  
             | script_block [ -args argument_array ]  
             | string [ command_parameters ]  
             }  
  ]  
]  
[ -? | -Help ]  
```  
  
## <a name="arguments"></a>引数  
 **-NoLogo**  
 **sqlps** ユーティリティの起動時に著作権画面を表示しないように指定します。  
  
 **-NoExit**  
 スタートアップ コマンドの完了後に **sqlps** ユーティリティの実行を継続するように指定します。  
  
 **-NoProfile**  
 **sqlps** ユーティリティがユーザー プロファイルを読み込まないように指定します。 ユーザー プロファイルには、複数の PowerShell セッションで共通して使用する別名、関数、および変数が記録されます。  
  
 **-OutPutFormat** { **Text** | **XML** }  
 **sqlps** ユーティリティの出力を、テキスト文字列形式 (**Text**) にするか、シリアル化された CLIXML 形式 (**XML**) にするかを指定します。  
  
 **-InPutFormat** { **Text** | **XML** }  
 **sqlps** ユーティリティへの入力を、テキスト文字列形式 (**Text**) にするか、シリアル化された CLIXML 形式 (**XML**) にするかを指定します。  
  
 **-Command**  
 **sqlps** ユーティリティで実行するコマンドを指定します。 **-NoExit** が同時に指定されていない限り、 **sqlps** ユーティリティはこのコマンドの実行後に終了します。 **-Command**の後にはその他のスイッチを指定しないでください。指定すると、コマンド パラメーターとして読み取られます。  
  
 **-**  
 **-Command-** は、 **sqlps** ユーティリティで入力を標準入力から読み取ることを指定します。  
  
 *script_block* [ **-args***argument_array* ]  
 PowerShell コマンドのブロックを実行することを指定します。ブロックは中かっこ {} で囲む必要があります。 *Script_block* を指定できるのは、 **sqlps** ユーティリティを **PowerShell** または他の **sqlps** ユーティリティ セッションから呼び出すときだけです。 *argument_array* は、 *script_block*内の PowerShell コマンドの引数を含む PowerShell 変数の配列です。  
  
 *string* [ *command_parameters* ]  
 実行する PowerShell コマンドを含む文字列を指定します。 形式を使用して**"& {***コマンド***}"**です。 引用符は文字列を示し、呼び出し演算子 (&) は **sqlps** ユーティリティにコマンドを実行させます。  
  
 [ **-?** | **-Help** ]  
 **sqlps** ユーティリティ オプションの構文の概要を表示します。  
  
## <a name="remarks"></a>解説  
 **sqlps** ユーティリティは、PowerShell 環境 (PowerShell.exe) を起動し、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell モジュールを読み込みます。 このモジュール ( **sqlps**) は、以下の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell スナップインの読み込みと登録を行います。  
  
-   Microsoft.SqlServer.Management.PSProvider.dll  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell プロバイダーおよび関連するコマンドレット ( **Encode-SqlName** や **Decode-SqlName**など) を実装します。  
  
-   Microsoft.SqlServer.Management.PSSnapin.dll  
  
     **Invoke-Sqlcmd** および **Invoke-PolicyEvaluation** コマンドレットを実装します。  
  
 **sqlps** ユーティリティを使用して、次の操作を行うことができます。  
  
-   PowerShell コマンドを対話的に実行する。  
  
-   PowerShell スクリプト ファイルを実行する。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コマンドレットを実行する。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダー パスを使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの階層内を移動する。  
  
 既定では、 **sqlps** ユーティリティ実行時のスクリプト実行ポリシーは **Restricted**に設定されます。 これにより、PowerShell スクリプトの実行が防止されます。 **Set-ExecutionPolicy** コマンドレットを使用すると、署名されたスクリプトまたは任意のスクリプトの実行を有効にすることができます。 信頼できるソースからのスクリプト以外は実行しないでください。また、適切な NTFS 権限を使用して、すべての入力ファイルと出力ファイルのセキュリティを保護してください。 PowerShell スクリプトの有効化の詳細については、「 [Windows PowerShell スクリプトの実行](http://go.microsoft.com/fwlink/?LinkId=103166)」を参照してください。  
  
 **および** に採用されていたバージョンの [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] sqlps [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ユーティリティは、Windows PowerShell 1.0 のミニシェルとして実装されていました。 ミニシェルには特定の制限があります。たとえば、ミニシェルによって読み込まれているスナップイン以外、ユーザーは読み込むことができません。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 以降のバージョンのユーティリティは、 **sqlps** モジュールを使用するように変更されており、このような制限は適用されません。  
  
## <a name="examples"></a>使用例  
 **A.既定でに sqlps ユーティリティを実行する著作権画面を表示せず、対話モード**  
  
```  
sqlps -NoLogo  
```  
  
 **B.コマンド プロンプトから SQL Server PowerShell スクリプトを実行します。**  
  
```  
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
 **C.コマンド プロンプトから SQL Server PowerShell スクリプトを実行し、スクリプト完了後も実行してください。**  
  
```  
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルの有効化または無効化](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)  
  
  
