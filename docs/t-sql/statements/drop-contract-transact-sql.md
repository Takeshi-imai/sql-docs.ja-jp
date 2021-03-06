---
title: "ドロップ コントラクト (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_CONTRACT_TSQL
- DROP CONTRACT
dev_langs:
- TSQL
helpviewer_keywords:
- dropping contracts
- removing contracts
- deleting contracts
- contracts [Service Broker], dropping
- DROP CONTRACT statement
ms.assetid: fdd0f81e-3c22-4cdf-9416-b4977a6ac3b6
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26d986a502dfa4436d44ff733a1cd6ff50355788
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="drop-contract-transact-sql"></a>DROP CONTRACT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のコントラクトをデータベースから削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP CONTRACT contract_name   
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *contract_name*  
 削除するコントラクトの名前を指定します。 サーバー名、データベース名、スキーマ名は指定できません。  
  
## <a name="remarks"></a>解説  
 サービスまたはメッセージ交換の優先度でコントラクトが参照されている場合は、コントラクトを削除できません。  
  
 コントラクトを削除するとき、そのコントラクトを使用している既存のメッセージ交換は、[!INCLUDE[ssSB](../../includes/sssb-md.md)] によってエラーと共に終了されます。  
  
## <a name="permissions"></a>権限  
 コントラクトを削除する権限は、既定ではコントラクトの所有者、db_ddladmin 固定データベース ロールまたは db_owner 固定データベース ロールのメンバー、および sysadmin 固定サーバー ロールのメンバーに与えられています。  
  
## <a name="examples"></a>使用例  
 次の例では、データベースからコントラクト `//Adventure-Works.com/Expenses/ExpenseSubmission` を削除します。  
  
```  
DROP CONTRACT   
    [//Adventure-Works.com/Expenses/ExpenseSubmission] ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER BROKER PRIORITY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [ALTER SERVICE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-service-transact-sql.md)   
 [コントラクト &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-contract-transact-sql.md)   
 [DROP BROKER PRIORITY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-broker-priority-transact-sql.md)   
 [サービス &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-service-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
