---
title: "sp_cycle_agent_errorlog (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sp_cycle_agent_errorlog
- sp_cycle_agent_errorlog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cycle_agent_errorlog
ms.assetid: 8aa96182-60b7-4d7b-b2a7-ccce70378c6e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6819b6d6258475cc3b4aa1d41880a71696262749
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="spcycleagenterrorlog-transact-sql"></a>sp_cycle_agent_errorlog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバーを再起動するときと同様に、現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント エラー ログ ファイルを閉じ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント エラー ログの拡張番号を使い回します。 新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント エラー ログには、新しいログが作成されたことを示す行が含まれます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cycle_agent_errorlog  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 たびに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントを起動すると、現在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント エラー ログの名前を変更する**SQLAgent.1**です。**SQLAgent.1**なります**SQLAgent.2**、 **SQLAgent.2**なります**SQLAgent.3**のようにします。 **sp_cycle_agent_errorlog**を停止してから、サーバーを起動しないで、エラー ログ ファイルを使い回すことができます。  
  
 このストアド プロシージャを実行する必要があります、 **msdb**データベース。  
  
## <a name="permissions"></a>権限  
 実行権限**sp_cycle_agent_errorlog**のメンバーに制限されます、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント エラー ログを使い回します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_cycle_agent_errorlog ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_cycle_errorlog &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql.md)  
  
  
