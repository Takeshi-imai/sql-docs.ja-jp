---
title: "Oracle スキーマをマッピングから SQL Server スキーマ (OracleToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc
caps.latest.revision: "8"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: On Demand
ms.openlocfilehash: 025f3f049b5efccb83e13d5baebacbe8b0fa2a1c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-oracle-schemas-to-sql-server-schemas-oracletosql"></a>SQL Server スキーマ (OracleToSQL) への Oracle スキーマのマッピング
Oracle は、各データベースは、1 つまたは複数のスキーマを持っています。 既定では、SSMA は Oracle スキーマ内のすべてのオブジェクトを移行、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマという名前のデータベースです。 ただし、Oracle スキーマ間のマッピングをカスタマイズすることができ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
## <a name="oracle-and-sql-server-schemas"></a>Oracle と SQL Server スキーマ  
Oracle データベースには、スキーマが含まれています。 インスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]それぞれが複数のスキーマを持つことができます、複数のデータベースが含まれています。  
  
Oracle の概念スキーマにマップ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースとそのスキーマのいずれかの概念です。 たとえば、Oracle がという名前のスキーマを含めることが**HR**です。 インスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]という名前のデータベースがあります**HR**は、そのデータベース内のスキーマです。 1 つのスキーマは、 **dbo** (またはデータベース所有者) スキーマ。 既定では、Oracle スキーマ**HR**にマップされます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースおよびスキーマ**HR.dbo**です。 SSMA を指す、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマとしてデータベースおよびスキーマの組み合わせ。  
  
Oracle 間のマッピングを変更して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマです。  
  
## <a name="modifying-the-target-database-and-schema"></a>ターゲット データベースおよびスキーマの変更  
SSMA に、使用可能な Oracle スキーマをマップできます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマです。  
  
**データベースおよびスキーマを変更するには**  
  
1.  Oracle メタデータ エクスプ ローラーで、次のように選択します。**スキーマ**です。  
  
    **スキーマ マッピング** タブは、個々 のデータベースを選択した場合にも使用可能な**スキーマ**フォルダー、または個別のスキーマです。 一覧で、**スキーマ マッピング** タブを選択したオブジェクトのカスタマイズします。  
  
2.  右側のウィンドウでをクリックして、**スキーマ マッピング**タブです。  
  
    すべての Oracle スキーマ、続くターゲット値の一覧が表示されます。 このターゲットは、2 部構成の表記法で表されます (*database.schema*) で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクトとデータを移行します。  
  
3.  選択を行い、をクリックするマッピングを含む行**変更**です。  
  
    **ターゲット スキーマの選択**ダイアログ ボックスで、使用可能な対象データベースとスキーマ、または型データベースおよびスキーマで 2 部構成の表記 (database.schema) で、テキスト ボックスの名前をクリックを参照することがあります**OK**です。  
  
4.  は、ターゲットの変更、**スキーマ マッピング**タブです。  
  
**マッピングのモード**  
  
-   SQL Server へのマッピング  
  
ソース データベースは、任意のターゲット データベースにマップできます。 既定では、ソース データベースがマップされているターゲットに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA を使用してを接続したデータベースです。 マップされているターゲット データベースが存在しないで[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、メッセージを使用するように求められますが、 **"データベースまたはスキーマがターゲットに存在しません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ。これが同期中に作成されます。か続行しますか?"** [はい] をクリックします。 同様に、[ターゲット] で、存在しないスキーマをスキーマをマップできる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]同期中に作成されるデータベース。  
  
## <a name="reverting-to-the-default-database-and-schema"></a>既定のデータベースとスキーマを元に戻す  
Oracle スキーマ間のマッピングをカスタマイズする場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマ、既定値に戻すマッピングを戻すことができます。  
  
**既定のデータベースとスキーマに戻すには**  
  
1.  スキーマのマッピング] タブで、[任意の行を選択し、をクリックして**既定値にリセット**既定のデータベースとスキーマを元に戻す。  
  
## <a name="next-steps"></a>Next Steps  
Oracle オブジェクトへの変換を分析するかどうかは[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト、することができます[変換レポートを作成する](http://msdn.microsoft.com/en-us/4de9bcf6-1346-4740-87f9-7f24a8226357)です。 それ以外の場合を実行できます[Oracle データベースのオブジェクトの定義の変換](http://msdn.microsoft.com/en-us/e021182d-31da-443d-b110-937f5db27272)に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト定義します。  
  
## <a name="see-also"></a>参照  
[SQL Server &#40;OracleToSQL&#41; への接続](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
[SQL Server &#40;OracleToSQL&#41; への Oracle データベースの移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
