---
title: "sp_OAStop (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_OAStop
- sp_OAStop_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAStop
ms.assetid: aa9eab66-c4f7-4ec7-9f0d-5d24d16da654
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7efcb85558f34ca1df934bb1fa97e94e99105d93
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spoastop-transact-sql"></a>sp_OAStop (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー全体の OLE オートメーション ストアド プロシージャの実行環境を停止します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_OAStop      
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0、失敗した場合は OLE オートメーション オブジェクトによって返される HRESULT の 0 以外の整数値を返します。  
  
 HRESULT のリターン コードの詳細については、次を参照してください。 [OLE オートメーションのリターン コードとエラー情報](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md)です。  
  
## <a name="remarks"></a>解説  
 OLE オートメーション ストアド プロシージャを使用しているすべてのクライアントで、1 つの実行環境が共有されます。 1 つのクライアントが呼び出す場合**sp_OAStop**のすべてのクライアントと共有実行環境は停止されます。 すべての呼び出しに、実行環境を停止すると後、 **sp_OACreate**実行環境を再起動します。  
  
## <a name="permissions"></a>Permissions  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、共有している OLE オートメーション実行環境を停止します。  
  
```  
EXEC sp_OAStop;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [OLE オートメーションのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE オートメーションのサンプル スクリプト](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
