---
title: "dbo.syscategories (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.syscategories_TSQL
- syscategories
- syscategories_TSQL
- dbo.syscategories
dev_langs:
- TSQL
helpviewer_keywords:
- syscategories system table
ms.assetid: eb2cb75c-dc58-4a5b-b329-664e9fe20ce0
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 870bd7217d215b7304ceed911d0dd8da2cca5837
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="dbosyscategories-transact-sql"></a>dbo.syscategories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、ジョブ、警告、オペレーターの分類に使用されるカテゴリを格納します。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|カテゴリの ID。|  
|**category_class**|**int**|カテゴリ内のアイテムの種類。<br /><br /> **1**ジョブを =<br /><br /> **2**アラートを =<br /><br /> **3** = 演算子|  
|**category_type**|**tinyint**|カテゴリの種類です。<br /><br /> **1** = ローカル<br /><br /> **2** = マルチ サーバー<br /><br /> **3** = なし|  
|**name**|**sysname**|カテゴリの名前。|  
  
  
