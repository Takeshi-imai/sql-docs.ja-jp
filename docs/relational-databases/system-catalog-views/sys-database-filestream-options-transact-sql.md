---
title: "sys.database_filestream_options (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- database_filestream_options
- sys.database_filestream_options_TSQL
- database_filestream_options_TSQL
- sys.database_filestream_options
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_filestream_options catalog view
ms.assetid: 3383c607-0bbc-456a-ab37-7230f4cbf0e9
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e142ba218eb5474bb45f488c87a4c41e0d2390a7
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdatabasefilestreamoptions-transact-sql"></a>sys.database_filestream_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  FileTable 内の有効化された FILESTREAM データに対する非トランザクション アクセスのレベルに関する情報を表示します。 SQL Server インスタンス内にあるデータベースごとに 1 行のデータを格納します。  
  
 Filetable の詳細については、次を参照してください。 [Filetable &#40;です。SQL Server &#41;](../../relational-databases/blob/filetables-sql-server.md).  
  
  
|列|型|Description|  
|------------|----------|-----------------|  
|**database_id**|**int**|データベースの ID。 この値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内で一意になっています。|  
|**directory_name**|**nvarchar (255)**|すべての FileTable 名前空間のデータベース レベルのディレクトリです。|  
|**non_transacted_access**|**tinyint**|有効化されている FILESTREAM データへの非トランザクション アクセスのレベルです。 アクセスのレベルがの NON_TRANSACTED_ACCESS オプションで設定されている、 **CREATE DATABASE**または**ALTER DATABASE**ステートメントです。<br /><br /> この設定は、次のいずれかの値になります。<br /><br /> 0 – 無効。 これが既定値です。 このレベルは、値を提供することにより設定**OFF**の**NON_TRANSACTED_ACCESS**オプション。<br /><br /> 1 – 読み取り専用アクセス。 このレベルは、値を提供することにより設定**READ_ONLY**の**NON_TRANSACTED_ACCESS**オプション。<br /><br /> 3 – 完全アクセス。 このレベルは、値を提供することにより設定**完全**の**NON_TRANSACTED_ACCESS**オプション。<br /><br /> 5 - READONLY に移行中。<br /><br /> 6 – OFF に移行中。|  
|**non_transacted_access_desc**|**nvarchar(60)**|Non_transacted_access で識別される非トランザクション アクセスのレベルの説明です。<br /><br /> この設定は、次のいずれかの値になります。<br /><br /> NONE – これは既定値です。<br /><br /> READ_ONLY<br /><br /> FULL<br /><br /> IN_TRANSITION_TO_READ_ONLY<br /><br /> IN_TRANSITION_TO_OFF|  
  
## <a name="see-also"></a>参照  
 [FileTable の前提条件の有効化](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
  
