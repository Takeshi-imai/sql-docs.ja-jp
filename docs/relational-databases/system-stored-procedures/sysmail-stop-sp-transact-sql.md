---
title: sysmail_stop_sp (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_stop_sp_TSQL
- sysmail_stop_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_stop_sp
ms.assetid: 045ee36f-5bf0-4626-b5ee-e84db06ce16f
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eddddd99576f27cc0252ab77a8b71098915526fc
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysmailstopsp-transact-sql"></a>sysmail_stop_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  停止してデータベース メールを停止、[!INCLUDE[ssSB](../../includes/sssb-md.md)]外部プログラムによって使用されるオブジェクト。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_stop_sp  
```  
  
## <a name="arguments"></a>引数  
 なし  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 このストアド プロシージャは、 **msdb**データベース。  
  
 このストアド プロシージャは、送信メッセージ要求を保持し、オフにするデータベース メール キューを停止[!INCLUDE[ssSB](../../includes/sssb-md.md)]外部プログラムのライセンス認証します。  
  
 キューが停止すると、データベース メール外部プログラムではメッセージが処理されなくなります。 このストアド プロシージャを使用すると、トラブルシューティングやメンテナンスの目的でデータベース メールを停止できます。  
  
 データベース メールを開始するには使用**sysmail_start_sp**です。 注意して**sp_send_dbmail**もメール、[!INCLUDE[ssSB](../../includes/sssb-md.md)]オブジェクトを停止します。  
  
> [!NOTE]  
>  このストアド プロシージャは、データベース メールのキューだけを停止します。 このストアド プロシージャは非アクティブ化できません[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ データベースに配信します。 このストアド プロシージャでは、外部からのアクセスを縮小するために、データベース メールの拡張ストアド プロシージャを無効にすることはできません。 拡張ストアド プロシージャを無効にするを参照してください、 [Database Mail XPs オプション](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)の**sp_configure**システム ストアド プロシージャです。  
  
## <a name="permissions"></a>権限  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、データベース メールでの停止、 **msdb**データベース。 ここではデータベース メールが有効になっていることを前提としています。  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_stop_sp ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_start_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [データベース メールのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
