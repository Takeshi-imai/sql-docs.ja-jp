---
title: "付録 - 1 (MySQLToSQL) |Microsoft ドキュメント"
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
ms.assetid: 2d22766d-ff09-420d-ae7c-13b443e28bd0
caps.latest.revision: "10"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: feaa4b29266246702290065e851d33df7b09e3e7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="appendix---1-mysqltosql"></a>付録 - 1 (MySQLToSQL)
SSMA コンソール コマンド ライン オプションの簡易表示:  
  
|Sl です。 不可。|スイッチ|必須/省略可能|引数を切り替える|指定できる値|  
|-----------|----------|-------------|-------------------|--------------------|  
|@shouldalert|-s/スクリプト|可|scriptfile|有効な XML ファイルの名前。<br /><br />スクリプトの定義ファイルのコンソールです。|  
|2|-v/変数|不可|variablevaluefile|有効な XML ファイルの名前。<br /><br />変数をスクリプト ファイルで使用する場合は、このファイルを指定する必要があります。|  
|3|-c/serverconnection|不可|serverconnectionfile|有効な XML ファイルの名前。<br /><br />このファイルには、サーバーの接続情報が含まれています。|  
|4|-x/xmloutput|不可|xmloutputfile|このオプションでは、XML 形式でのコンソール出力を示します。 このオプションが指定されていない場合、既定の出力はテキスト形式です。<br /><br />Xmloutputfile が指定されていない場合、XML 出力は STDOUT に送られます。<br /><br />Xmloutputfile は、XML 形式で、コンソール出力の書き込み先となるファイルの名前です。|  
|5|-l/ログ|不可|logfile|有効なファイル名。|  
|6|-e/projectenvironment|不可|projectenvironmentfolder|SSMA プロジェクト環境ファイルを含む有効なフォルダー名です。|  
|7|-p/securepassword|不可|-、/add {< server_id > [,... n] (& a) #124; すべて} – c &#124; serverconnection < サーバー接続ファイル > [-v &#124; 変数 < 変数値ファイル >] [-o/上書き]<br /><br />内の複数の<br /><br />-、/add {< server_id > [,... n] (& a) #124; すべて} – s &#124; スクリプト < スクリプト ファイル > [-v &#124; 変数 < 変数値ファイル >] [-o/上書き]<br /><br />– r/削除 {< server_id > [,... n] (& a) #124; すべて}<br /><br />-l/一覧表示<br /><br />– e/エクスポート {< サーバー id > [,... n] (& a) #124; すべて} < 暗号化パスワード - ファイル ><br /><br />– i/インポート {< サーバー id > [,... n] (& a) #124; すべて} < 暗号化パスワード ファイルに >|指定した場合、このオプションをその他のオプションと組み合わされていない必要があります。<br /><br />サーバー id: {string} サーバーの一意の ID が提供されます。<br /><br />ファイル サーバーに接続: サーバーの定義ファイル (serverconnectionfile または scriptfile)。<br /><br />変数値ファイル: クエリ変数の定義ファイルし、ファイル サーバーに接続で使用します。<br /><br />暗号化されたパスワード ファイル: ユーザーが指定したパス フレーズを使用して暗号化のサーバーのパスワード ファイルです。|  
|8|-?|不可|該当なし|該当なし|  
  
## <a name="see-also"></a>参照  
[SSMA コンソール (MySQL) を実行します。](http://msdn.microsoft.com/en-us/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
