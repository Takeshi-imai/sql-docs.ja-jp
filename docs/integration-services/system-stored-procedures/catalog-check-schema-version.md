---
title: catalog.check_schema_version | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: e0d5e9f5-59c6-4118-87b5-4aa5c37a7df6
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 10ec93a390173e089965e6f984c3725fb675748e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="catalogcheckschemaversion"></a>catalog.check_schema_version
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  SSISDB カタログ スキーマと [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] バイナリ (ISServerExec および SQLCLR アセンブリ) に互換性があるかどうかを示します。  
  
 スキーマとバイナリに互換性がない場合、ISServerExec.exc でエラー メッセージが記録されます。  
  
 SSISDB スキーマのバージョンは、修正プログラムや更新プログラムの適用時にスキーマが変更された場合に増加します。 SSISDB バックアップの復元後にこのストアド プロシージャを実行して、スキーマとバイナリに互換性があるようにすることをお勧めします。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.check_schema_version [@use32bitruntime = ] use32bitruntime  
```  
  
## <a name="arguments"></a>引数  
 [ @use32bitruntime= ] *use32bitruntime*  
 パラメーターが **True** の場合、32 ビット バージョンの dtexec が呼び出されます。 *use32bitruntime* は、**Bool** です。  
  
## <a name="result-set"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限が必要です。  
  
-   **ssis_admin** データベース ロールのメンバーシップ。  
  
  
