---
title: "Pdo::exec |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 359a87c6-c13a-4518-8f23-a922e7f3b171
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 48b1d6f918d87d2ad65b4be8b47a5a23975d1811
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="pdoexec"></a>PDO::exec
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

1 回の関数呼び出しで SQL ステートメントを準備および実行し、ステートメントの影響を受けた行数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
int PDO::exec ($statement)  
```  
  
#### <a name="parameters"></a>パラメーター  
*$statement*: 実行する SQL ステートメントを含む文字列です。  
  
## <a name="return-value"></a>戻り値  
影響を受けた行数を報告する整数です。  
  
## <a name="remarks"></a>解説  
*$statement* に複数の SQL ステートメントが含まれる場合、最後のステートメントの影響を受ける行数のみを返します。  
  
PDO::exec では SELECT ステートメントの結果は返しません。  
  
PDO::exec の動作に影響する属性は次のとおりです。  
  
-   PDO::ATTR_DEFAULT_FETCH_MODE  
  
-   PDO::SQLSRV_ATTR_ENCODING  
  
-   PDO::SQLSRV_ATTR_QUERY_TIMEOUT  
  
詳細については、「 [PDO::setAttribute](../../connect/php/pdo-setattribute.md) 」をご覧ください。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
この例では、Table1 の col1 に 'xxxyy' がある行を削除します。 次いで例では削除した行数を報告します。  
  
```  
<?php  
   $c = new PDO( "sqlsrv:server=(local)");  
  
   $c->exec("use Test");  
   $ret = $c->exec("delete from Table1 where col1 = 'xxxyy'");  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
