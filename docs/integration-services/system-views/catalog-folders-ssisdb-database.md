---
title: "catalog.folders (SSISDB データベース) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 21a37c16-60aa-4b3f-8bca-ac90ad1697ac
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e6ac40d88cd99c30f8cb5d80037d7e8ae4195bdd
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="catalogfolders-ssisdb-database"></a>catalog.folders (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのフォルダーを表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|id|**bigint**|フォルダーの一意識別子。|  
|NAME|**sysname(nvarchar(128)**|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログ内で一意のフォルダーの名前。|  
|description|**nvarchar(1024)**|フォルダーの説明。|  
|created_by_sid|**varbinary(85)**|フォルダーを作成したユーザーの一意なセキュリティ識別子 (SID)。|  
|created_by_name|**nvarchar(128)**|フォルダーを作成したユーザーの名前。|  
|created_time|**datetimeoffset(7)**|フォルダーが作成された日時。|  
  
## <a name="remarks"></a>Remarks  
 このビューは、カタログの各フォルダーの行を表示します。  
  
## <a name="permissions"></a>アクセス許可  
 このビューには、次の権限のいずれかが必要です。  
  
-   フォルダーの READ 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  
