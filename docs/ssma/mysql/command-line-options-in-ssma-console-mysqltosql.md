---
title: "SSMA コンソール (MySQLToSQL) でのコマンド ライン オプション |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
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
helpviewer_keywords:
- Command line options, help option
- Command line options, log file option
- Command line options, project environment folder option
- Command line options, script file option
- Command line options, secure password option
- Command line options, SecurePassword help option
- Command line options, server connection file option
- Command line options, variable value file option
- Command line options, XML output option
ms.assetid: a2310b10-68ad-4285-a08b-c8694cf84416
caps.latest.revision: "12"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aa2e0210a3d59e41b9adf9d44b593e3bc83e9aef
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-options-in-ssma-console-mysqltosql"></a>SSMA コンソール (MySQLToSQL) でのコマンド ライン オプション
Microsoft を実行し、SSMA 動作を制御する堅牢な一連のコマンド ライン オプションを提供します。 次のセクションでは、同じを詳しく説明します。  
  
## <a name="command-line-options-in-ssma-console"></a>SSMA コンソールでのコマンド ライン オプション  
コンソールは、コマンドのオプションは、ドキュメントに記載します。  
  
このセクションの目的で用語 'option' とも呼びます 'switch' です。  
  
オプションは、小文字は区別されず、いずれかで始めることは '**-**'、'**/**' 文字です。  
  
オプションを指定する場合、対応するオプション パラメーターを指定する必須になります。  
  
オプション パラメーターは、オプションの文字から空白の領域で区切る必要があります。  
  
**構文例:**  
  
`C:\> SSMAforMySQLConsole.EXE -s scriptfile`  
  
`C:\> SSMAforMySQLConsole.EXE -s “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\AssessmentReportGenerationSample.xml” –v “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\VariableValueFileSample.xml” –c “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ServersConnectionFileSample.xml”`  
  
二重引用符で囲まれた空白を含むフォルダーまたはファイルの名前を指定する必要があります。  
  
コマンドラインのエントリとエラー メッセージの出力は STDOUT にまたは指定されたファイル内に格納されます。  
  
### <a name="script-file-option-sscript"></a>スクリプト ファイルのオプション: – s/スクリプト  
必須のスイッチでは、スクリプト ファイルのパスと名前は、SSMA によって実行されるコマンドのシーケンスのスクリプトを指定します。  
  
**構文例:**  
  
`C:\>SSMAforMySQLConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="variable-value-file-option-vvariable"></a>– V/変数の変数値のファイル オプション:  
このファイルには、スクリプト ファイルで使用される変数が構成されています。 これは、省略可能なスイッチです。 変数がない変数ファイルで宣言されているし、スクリプト ファイルで使用される、アプリケーションが、エラーが発生し、コンソールの実行を終了します。  
  
**構文例:**  
  
変数は、おそらく 1 つで、既定値と該当する場合に、インスタンス固有値を持つ別の複数の変数値ファイルで定義されています。 変数の重複がある場合に、コマンドライン引数で指定された最後の変数ファイルは、基本設定を受け取る。  
  
`C:\>SSMAforMySQLConsole.EXE -s`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml” –v c:\migration`  
  
`projects\global_variablevaluefile.xml –v “c:\migrationprojects\instance_variablevaluefile.xml”`  
  
### <a name="server-connection-file-option-cserverconnection"></a>サーバー接続のファイル オプション: – c/serverconnection  
このファイルには、各サーバーのサーバー接続情報が含まれています。 各サーバーの定義は、id。 一意なサーバーによって識別されます。 サーバーの Id が接続用のスクリプト ファイルで参照されている関連するコマンド。  
  
サーバーの定義は、サーバー接続のファイルやスクリプト ファイルの一部にすることができます。 スクリプト ファイル内のサーバー id は、サーバー接続ファイルに優先されるサーバー id の重複がある場合にします。  
  
**構文例:**  
  
サーバー Id は、スクリプト ファイルで使用して、別のサーバー接続ファイルで定義されている、サーバー接続ファイルは、変数値ファイルで定義されている変数を使用します。  
  
`C:\>SSMAforMySQLConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –v`  
  
`c:\SsmaProjects\myvaluefile1.xml –c`  
  
`c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
サーバーの定義がスクリプト ファイルに埋め込まれます。  
  
`C:\>SSMAforMySQLConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>XML 出力のオプション: x/xmloutput [xmloutputfile]  
このコマンドはコンソールにするか、xml ファイルを xml 形式でコマンドの出力メッセージを出力するために使用されます。  
  
2 つのオプション使用できるが、xmloutput viz。  
  
-   Xmloutput スイッチの後にファイル パスが指定した場合は、ファイルに出力がリダイレクトされます。  
  
    **構文例:**  
  
    `C:\>SSMAforMySQLConsole.EXE –s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –x d:\xmloutput\project1output.xml`  
  
-   Xmloutput スイッチの後にファイル パスが指定されていない場合は、コンソール自体に、xmlout が表示されます。  
  
    **構文例:**  
  
    `C:\>SSMAforMySQLConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –xmloutput`  
  
### <a name="log-file-option-llog"></a>– L/ログのログ ファイルのオプション:  
コンソール アプリケーションでのすべての SSMA 操作は、ログ ファイルに記録を取得します。 これは、省略可能なスイッチです。 ログ ファイルとそのパスをコマンドラインで指定する場合、ログが指定された場所に生成を取得します。 それ以外の場合、これは既定の場所で生成されたを取得します。  
  
**構文例:**  
  
`C:\>SSMAforMySQLConsole.EXE`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option-eprojectenvironment"></a>プロジェクトの環境のフォルダー オプション: – e/projectenvironment  
これは、環境設定のプロジェクト フォルダーに現在の SSMA プロジェクトを示します。 このスイッチは省略できます。  
  
**構文例:**  
  
`C:\>SSMAforMySQLConsole.EXE –s`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –e c:\SsmaProjects\CommonEnvironment`  
  
### <a name="secure-password-option-psecurepassword"></a>セキュリティで保護されたパスワードのオプション: – p/securepassword  
このオプションでは、サーバー接続の暗号化されたパスワードを指定します。 その他のすべてのオプションとは異なる: オプションで、スクリプトの実行も移行関連のあらゆる作業に役立ちますが、移行プロジェクトで使用するサーバー接続のパスワードの暗号化の管理を支援します。  
  
コマンド ライン パラメーターとして、他のオプションやパスワードを入力することはできません。 それ以外の場合、エラーが発生します。 詳細についてを参照してください、[管理パスワード](http://msdn.microsoft.com/en-us/4ffbc587-ea3f-49ad-bc42-a654f672325e)セクションです。  
  
次のサブ オプションはサポートされて`–p/securepassword`:  
  
-   パスワードを追加するには、指定したサーバー ID に対して、またはサーバー接続ファイルで定義されているすべてのサーバー Id の記憶域を保護します。 既に存在する場合、更新プログラムの下のオプションのパスワードを上書きします。  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}` `-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   指定したサーバー ID のまたはすべてのサーバー Id の保護された記憶域から暗号化されたパスワードを削除します。  
  
    `–p/securepassword –r/remove {<server_id> [, …n] | all}`  
  
-   パスワードの暗号化をサーバー Id の一覧を表示するには。  
  
    `–p/securepassword –l/list`  
  
-   暗号化されたファイルを保護されたストレージに格納されているパスワードをエクスポートします。 このファイルは、パス フレーズをユーザー指定で暗号化されます。  
  
    `–p/securepassword –e/export {<server-id> [, …n] | all} <encrypted-password -file>`  
  
-   暗号化、以前エクスポートされたファイルが、ユーザーが指定したパスフレーズを使用してローカルの保護されたストレージにインポートされます。 ファイルが暗号化解除は、さらに、ローカル コンピューターの暗号化は、新しいファイルに格納されます。  
  
    `–p/securepassword –i/import {<server-id> [, …n] | all} <encrypted-password -file>`  
  
    コンマ区切り記号を使用して、複数のサーバー Id を指定できます。  
  
### <a name="help-option-help"></a>ヘルプ オプション: –?/help  
SSMA コンソールのオプションの構文の概要が表示されます。  
  
`C:\>SSMAforMySQLConsole.EXE -?`  
  
SSMA コンソール コマンド ライン オプションの表形式の表示を参照してください[付録 - 1 &#40;です。MySQLToSQL &#41;](../../ssma/mysql/appendix-1-mysqltosql.md).  
  
### <a name="securepassword-help-option-securepassword--help"></a>SecurePassword ヘルプ オプション: – securepassword-?/help  
SSMA コンソールのオプションの構文の概要が表示されます。  
  
`C:\>SSMAforMySQLConsole.EXE -securepassword -?`  
  
SSMA コンソール コマンド ライン オプションの表形式の表示を参照してください[付録 - 1 &#40;です。MySQLToSQL &#41;](../../ssma/mysql/appendix-1-mysqltosql.md)  
  
### <a name="next-step"></a>次の手順  
次の手順は、プロジェクトの要件によって異なります。  
  
-   パスワードまたはエクスポートを指定する/パスワードのインポートを参照してください[パスワードの管理 &#40;です。MySQLToSQL &#41;](../../ssma/mysql/managing-passwords-mysqltosql.md).  
  
-   レポートの生成に、次を参照してください。[レポートの生成 &#40;です。MySQLToSQL &#41;](../../ssma/mysql/generating-reports-mysqltosql.md).  
  
-   コンソールで問題をトラブルシューティングするには、次を参照してください。[トラブルシューティング &#40;です。MySQLToSQL &#41;](../../ssma/mysql/troubleshooting-mysqltosql.md).  
  
