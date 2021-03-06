---
title: "sqlsrv_configure |Microsoft ドキュメント"
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
apiname: sqlsrv_configure
apitype: NA
helpviewer_keywords:
- sqlsrv_configure
- API Reference, sqlsrv_configure
ms.assetid: 9393f975-a4ef-4c50-b4dd-14892fc55cc9
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 68ed443c80b2eff8405bb5419da132edf49a6807
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlsrvconfigure"></a>sqlsrv_configure
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

エラー処理とログ記録のオプションの設定を変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_configure( string $setting, mixed $value )  
```  
  
#### <a name="parameters"></a>パラメーター  
*$setting*: 構成する設定の名前です。 設定の一覧については、次の表を参照してください。  
  
*$value*: *$setting* パラメーターで指定された設定に適用する値です。 このパラメーターに指定できる値は、指定されている設定によって異なります。 次の表に、考えられる組み合わせを示します。  
  
|設定|$value パラメーターに使用可能な値 (かっこ内と同等の整数)|既定値|  
|-----------|------------------------------------------------------------------------------|-----------------|  
|ClientBufferMaxKBSize<sup>1</sup>|PHP メモリの上限に達するまでの負以外の数値。<br /><br />ゼロ (0) は、バッファーのサイズに制限がないことを意味します。|10240|  
|LogSeverity<sup>2</sup>|SQLSRV_LOG_SEVERITY_ALL (-1)<br /><br />SQLSRV_LOG_SEVERITY_ERROR (1)<br /><br />SQLSRV_LOG_SEVERITY_NOTICE (4)<br /><br />SQLSRV_LOG_SEVERITY_WARNING (2)|SQLSRV_LOG_SEVERITY_ERROR (1)|  
|LogSubsystems<sup>2</sup>|SQLSRV_LOG_SYSTEM_ALL (-1)<br /><br />SQLSRV_LOG_SYSTEM_CONN (2)<br /><br />SQLSRV_LOG_SYSTEM_INIT (1)<br /><br />SQLSRV_LOG_SYSTEM_OFF (0)<br /><br />SQLSRV_LOG_SYSTEM_STMT (4)<br /><br />SQLSRV_LOG_SYSTEM_UTIL (8)|SQLSRV_LOG_SYSTEM_OFF (0)|  
|WarningsReturnAsErrors<sup>3</sup>|**true** (1) または**false** (0)|**true** (1)|  
  
## <a name="return-value"></a>戻り値  
サポートされていない設定または値を使用して **sqlsrv_configure** 関数を呼び出すと、この関数は **false**を返します。 それ以外の場合は、 **true**を返します。  
  
## <a name="remarks"></a>解説  
(1) のクライアント側クエリの詳細については、次を参照してください。[カーソルの種類 &#40;です。SQLSRV ドライバー &#41;](../../connect/php/cursor-types-sqlsrv-driver.md).  
  
(2) のログ記録アクティビティの詳細については、次を参照してください。 [Logging Activity](../../connect/php/logging-activity.md)です。  
  
(3) のエラーおよび警告の処理の構成に関する詳細については、次を参照してください。[する方法: エラーおよび警告の処理、SQLSRV ドライバーを使用して構成する](../../connect/php/how-to-configure-error-and-warning-handling-using-the-sqlsrv-driver.md)です。  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[プログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md) 
  
