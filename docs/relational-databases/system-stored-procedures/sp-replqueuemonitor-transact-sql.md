---
title: "sp_replqueuemonitor (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_replqueuemonitor
- sp_replqueuemonitor_TSQL
helpviewer_keywords:
- sp_replqueuemonitor
ms.assetid: 6909a3f1-43a2-4df5-a6a5-9e6f347ac841
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bd29cdd9e22873dd7d10db99078f25ce7e15d55f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spreplqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  メッセージ キューを一覧表示、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キューまたは[!INCLUDE[msCoName](../../includes/msconame-md.md)]メッセージは、指定したパブリケーションに対するキュー更新サブスクリプションのキューです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] キューを使用している場合、このストアド プロシージャはサブスクライバー側のサブスクリプション データベース上で実行されます。 メッセージ キューイングを使用している場合、このストアド プロシージャはディストリビューター側のディストリビューション データベース上で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replqueuemonitor [ @publisher = ] 'publisher'  
    [ , [ @publisherdb = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @tranid = ] 'tranid' ]  
    [ , [ @queuetype = ] 'queuetype' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publisher**  =] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は NULL です。 サーバーはパブリッシング用に構成されている必要があります。 NULL はすべてのパブリッシャーを表します。  
  
 [  **@publisherdb**  =] **'***publisher_db***'** ]  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**、既定値は NULL です。 NULL はすべてのパブリケーション データベースを表します。  
  
 [  **@publication**  =] **'***パブリケーション***'** ]  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は NULL です。 NULL はすべてのパブリケーションを表します。  
  
 [  **@tranid**  =] **'***tranid***'** ]  
 トランザクション ID です。 *tranid*は**sysname**、既定値は NULL です。 NULL はすべてのトランザクションを表します。  
  
 [**@queuetype=** ] **'***queuetype***'** ]  
 トランザクションを格納するキューの種類です。 *queuetype*は**tinyint** 、既定値は**0**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|すべての種類のキューです。|  
|**1**|メッセージ キューイング (Message Queuing)|  
|**2**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キュー|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_replqueuemonitor**はスナップショット レプリケーションまたはトランザクション レプリケーションでは、キュー更新サブスクリプションで使用します。 SQL コマンドが含まれないキュー メッセージ、または SQL コマンドの一部であるキュー メッセージは表示されません。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_replqueuemonitor**です。  
  
## <a name="see-also"></a>参照  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
