---
title: PWDCOMPARE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PWDCOMPARE
- PWDCOMPARE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sa account
- passwords [SQL Server], blank
- PWDCOMPARE function [Transact-SQL]
ms.assetid: 5f84ff9e-c1ec-46aa-8501-50f854ebcc3a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 23b90a0d4a09fc2eb754dc5f298883ef4469ade5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="pwdcompare-transact-sql"></a>PWDCOMPARE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パスワードをハッシュして既存のパスワードのハッシュと比較します。 PWDCOMPARE を使用すると、空白の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン パスワードや、よくある脆弱なパスワードを検索できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
PWDCOMPARE ( 'clear_text_password'  
   , password_hash   
   [ , version ] )  
```  
  
## <a name="arguments"></a>引数  
 **'** *clear_text_password* **'**  
 暗号化されていないパスワードです。 *clear_text_password* is **sysname** (**nvarchar(128)**).  
  
 *password_hash*  
 パスワードの暗号化ハッシュです。 * password_hash * が varbinary (128)*です。  
  
 *version*  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降に移行されたが [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] システムには変換されていない [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 以前のログインからの値を *password_hash* が表している場合に、1 に設定される可能性がある、古いパラメーターです。 バージョン *は int*です。  
  
> [!CAUTION]  
>  このパラメーターは旧バージョンとの互換性を維持するために提供されていますが、パスワード ハッシュ BLOB は独自のバージョンの説明を含んでいるため、無視されます。 [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
 場合 1 を返しますのハッシュ、 clear_text_password *と一致する、 password_hash* パラメーター、および、そうでない場合は 0 です。  
  
## <a name="remarks"></a>Remarks  
 PWDCOMPARE 関数は、パスワード ハッシュの強度に対する脅威にはなりません。このテストは、最初のパラメーターとして渡されるパスワードを使用してログインしようとした場合に実行されるテストと同じテストです。  
  
 PWDCOMPARE** 包含データベース ユーザーのパスワードを使用することはできません。 該当する包含データベースは存在しません。  
  
## <a name="permissions"></a>アクセス許可  
 PWDENCRYPT は、パブリックで使用できます。  
  
 sys.sql_logins の password_hash 列を調べるには CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-identifying-logins-that-have-no-passwords"></a>A. パスワードがないログインを特定する  
 次の例では、パスワードがない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを特定します。  
  
```  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('', password_hash) = 1 ;  
```  
  
### <a name="b-searching-for-common-passwords"></a>B. よくあるパスワードを検索する  
 よくあるパスワードを見つけて変更できるように検索するには、そのパスワードを最初のパラメーターとして指定します。 たとえば、次のステートメントを実行すると、`password` として指定されているパスワードが検索されます。  
  
```  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('password', password_hash) = 1 ;  
```  
  
## <a name="see-also"></a>参照  
 [PWDENCRYPT &#40;Transact-SQL&#41;](../../t-sql/functions/pwdencrypt-transact-sql.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
