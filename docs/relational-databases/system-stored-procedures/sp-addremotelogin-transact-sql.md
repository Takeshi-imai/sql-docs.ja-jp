---
title: "sp_addremotelogin (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_addremotelogin_TSQL
- sp_addremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addremotelogin
ms.assetid: 71b7cd36-a17d-4b12-b102-10aeb0f9268b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5024781fdcfb26420432e3eae914dc1ae6c1f958
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spaddremotelogin-transact-sql"></a>sp_addremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ローカル サーバーに新しいリモート ログイン ID を追加します。 これにより、リモート サーバーがリモート プロシージャ呼び出しに接続して、これを実行できるようになります。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]代わりに、リンク サーバーとリンク サーバー ストアド プロシージャを使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @remoteserver  **=**  ] **'***remoteserver***'**  
 リモート ログインが適用されるリモート サーバーの名前を指定します。 *remoteserver*は**sysname**、既定値はありません。 だけの場合*remoteserver*が指定されているすべてのユーザーに*remoteserver*ローカル サーバーに同じ名前の既存のログインにマップされます。 このサーバーは、ローカル サーバーが認識している必要があります。 Sp_addserver を使用してこれを追加します。 ときにユーザーに*remoteserver*を実行しているローカル サーバーに接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で自分のログインと一致するローカル ログインとして接続するリモート ストアド プロシージャを実行する*remoteserver*. *remoteserver*リモート プロシージャ呼び出しを開始するサーバーです。  
  
 [ @loginame  **=**  ] **'***ログイン***'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンス上のユーザーのログイン ID を指定します。 *ログイン*は**sysname**、既定値は NULL です。 *ログイン*のローカル インスタンスに既に存在する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 場合*ログイン*が指定されているすべてのユーザーに*remoteserver*その特定のローカル ログインにマップされます。 ときにユーザーに*remoteserver*のローカル インスタンスに接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]として接続するリモート ストアド プロシージャを実行する*ログイン*です。  
  
 [ @remotename  **=**  ] **'***remote_name***'**  
 リモート サーバーにおけるユーザーのログイン ID を指定します。 *remote_name*は**sysname**、既定値は NULL です。 *remote_name*上に存在する必要があります*remoteserver*です。 場合*remote_name*指定すると、特定のユーザー *remote_name*にマップされて*ログイン*ローカル サーバーにします。 ときに*remote_name*で*remoteserver*のローカル インスタンスに接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]として接続するリモート ストアド プロシージャを実行する*ログイン*です。 ログイン ID *remote_name* 、リモート サーバー上のログイン ID と異なる場合が*ログイン*です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 分散クエリを実行するには、sp_addlinkedsrvlogin を使用します。  
  
 sp_addremotelogin は、ユーザー定義のトランザクション内で使用できません。  
  
## <a name="permissions"></a>Permissions  
 Sp_addremotelogin を実行できるは、sysadmin、securityadmin 固定サーバー ロールのメンバーだけです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-mapping-one-to-one"></a>A. 一対一でマップする  
 次の例では、リモート名をマップするローカル名の場合に、リモート サーバー`ACCOUNTS`とローカル サーバーが同じユーザー ログインが与えられています。  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-mapping-many-to-one"></a>B. 多対一でマップする  
 次の例では、リモート サーバー `ACCOUNTS` のすべてのユーザーを、ローカル ID `Albert` にマップするエントリを作成します。  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-using-explicit-one-to-one-mapping"></a>C. 明示的に一対一でマップする  
 次の例は、リモート ユーザーからのリモート ログインをマップ`Chris`、リモート サーバーで`ACCOUNTS`をローカルのユーザー`salesmgr`です。  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>参照  
 [sp_addlinkedsrvlogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_helpremotelogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
