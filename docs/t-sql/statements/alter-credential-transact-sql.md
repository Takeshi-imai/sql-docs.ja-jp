---
title: "ALTER 資格情報 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/19/2015
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
- ALTER CREDENTIAL
- ALTER_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], credentials
- credentials [SQL Server], ALTER CREDENTIAL statement
- modifying credentials
- authentication [SQL Server], credentials
- ALTER CREDENTIAL statement
ms.assetid: b08899a6-c09e-4af4-91aa-a978ada79264
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d01e5460b01790ba6b7ac59b25e7726399522165
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-credential-transact-sql"></a>ALTER CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  資格情報のプロパティを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER CREDENTIAL credential_name WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
```  
  
## <a name="arguments"></a>引数  
 *credential_name*  
 変更する資格情報の名前を指定します。  
  
 IDENTITY **='***identity_name***'**  
 サーバーの外部に接続するときに使用するアカウントの名前を指定します。  
  
 シークレット**='***シークレット***'**  
 送信の認証に必要なシークレットを指定します。 *シークレット*は省略可能です。  
  
## <a name="remarks"></a>解説  
 資格情報が変更されたとき、両方の値*identity_name*と*シークレット*リセットされます。 SECRET 引数を省略すると、格納されているシークレットの値は NULL に設定されます。  
  
 シークレットは、サービス マスター_キーを使用して暗号化されます。 サービス マスター キーが再生成された場合、シークレットは新しいサービス マスター キーを使って再暗号化されます。  
  
 資格情報に関する情報は、 **sys.credentials**カタログ ビューです。  
  
## <a name="permissions"></a>Permissions  
 ALTER ANY CREDENTIAL 権限が必要です。 資格情報がシステム資格情報の場合は、CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-password-of-a-credential"></a>A. 資格情報のパスワードを変更する  
 次の例と呼ばれる、資格情報に格納されているシークレットを変更する`Saddles`です。 資格情報には、Windows ログイン `RettigB` とそのパスワードが含まれています。 新しいパスワードは、SECRET 句を使って資格情報に追加されます。  
  
```  
ALTER CREDENTIAL Saddles WITH IDENTITY = 'RettigB',   
    SECRET = 'sdrlk8$40-dksli87nNN8';  
GO  
```  
  
### <a name="b-removing-the-password-from-a-credential"></a>B. 資格情報からパスワードを削除する  
 次の例では、`Frames` という資格情報からパスワードを削除します。 資格情報には、Windows ログイン `Aboulrus8` とパスワードが含まれています。 SECRET オプションを指定しないので、ステートメントを実行した後、資格情報のパスワードは NULL になります。  
  
```  
ALTER CREDENTIAL Frames WITH IDENTITY = 'Aboulrus8';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [資格情報 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-credential-transact-sql.md)   
 [ALTER データベース スコープの資格情報 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
