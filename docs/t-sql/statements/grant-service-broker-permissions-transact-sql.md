---
title: "GRANT Service Broker の権限 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
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
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server], Service Broker
- routes [Service Broker], permissions
- Service Broker, permissions
- GRANT statement, Service Broker
- remote service bindings [Service Broker], permissions
- message types [Service Broker], permissions
- contracts [Service Broker], permissions
ms.assetid: c5579976-97c4-4123-be0c-d0b98a9e38fb
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0383e0b5446537b77e02ce4b8e4d3e54c850bdd1
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="grant-service-broker-permissions-transact-sql"></a>GRANT (Service Broker の権限の許可) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Service Broker コントラクト、メッセージ型、リモート バインド、ルート、またはサービスに対する権限を許可します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
GRANT permission  [ ,...n ] ON  
    {    
              [ CONTRACT :: contract_name ]   
       | [ MESSAGE TYPE :: message_type_name ]    
       | [ REMOTE SERVICE BINDING :: remote_binding_name ]    
       | [ ROUTE :: route_name ]   
       | [ SERVICE :: service_name ]      
    }  
    TO database_principal [ ,...n ]   
    [ WITH GRANT OPTION ]  
        [ AS granting_principal ]  
```  
  
## <a name="arguments"></a>引数  
 *permission*  
 Service Broker のセキュリティ保護可能なリソースに対して許可できる権限を指定します。  下の表をご覧ください。  
  
 コントラクト **:: * * * contract_name*  
 権限を許可するコントラクトを指定します。 スコープ修飾子"::"が必要です。  
  
 MESSAGE TYPE **::***message_type_name*  
 権限を許可するメッセージ型を指定します。 スコープ修飾子 "::" が必要です。  
  
 REMOTE SERVICE BINDING **:: * * * remote_binding_name*  
 権限を許可するリモート サービス バインドを指定します。 スコープ修飾子 "::" が必要です。  
  
 ROUTE **::***route_name*  
 権限を許可するルートを指定します。 スコープ修飾子 "::" が必要です。  
  
 サービス **:: * * * service_name*  
 権限を許可するサービスを指定します。 スコープ修飾子 "::" が必要です。  
  
 *database_principal*  
 権限を許可するプリンシパルを指定します。 次のいずれかです。  
  
-   データベース ユーザー  
  
-   データベース ロール (database role)  
  
-   アプリケーション ロール (application role)  
  
-   Windows ログインにマップされるデータベース ユーザー  
  
-   Windows グループにマップされるデータベース ユーザー  
  
-   証明書にマップされるデータベース ユーザー  
  
-   非対称キーにマップされているデータベース ユーザー  
  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
 GRANT OPTION  
 権限が許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
 *granting_principal*  
 このクエリを実行するプリンシパルが権限を許可する権利を取得した、元のプリンシパルを指定します。 次のいずれかです。  
  
-   データベース ユーザー  
  
-   データベース ロール (database role)  
  
-   アプリケーション ロール (application role)  
  
-   Windows ログインにマップされるデータベース ユーザー  
  
-   Windows グループにマップされるデータベース ユーザー  
  
-   証明書にマップされるデータベース ユーザー  
  
-   非対称キーにマップされているデータベース ユーザー  
  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
## <a name="remarks"></a>解説  
  
## <a name="service-broker-contracts"></a>Service Broker コントラクト  
 Service Broker コントラクトは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次に、Service Broker コントラクトで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に一覧で示します。  
  
|Service Broker コントラクト権限|権限が含まれる Service Broker コントラクト権限|権限が含まれるデータベース権限|  
|----------------------------------------|---------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CONTRACT|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-message-types"></a>Service Broker メッセージ型  
 Service Broker メッセージ型は、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次に、Service Broker メッセージ型で許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に一覧で示します。  
  
|Service Broker メッセージ型権限|権限が含まれる Service Broker メッセージ型権限|権限が含まれるデータベース権限|  
|--------------------------------------------|-------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY MESSAGE TYPE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-remote-service-bindings"></a>Service Broker リモート サービス バインド  
 Service Broker リモート サービス バインドは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次に、Service Broker のリモート サービス バインドで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に一覧で示します。  
  
|Service Broker リモート サービス バインド権限|権限が含まれる Service Broker リモート サービス バインド権限|権限が含まれるデータベース権限|  
|------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY REMOTE SERVICE BINDING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-routes"></a>Service Broker ルート  
 Service Broker ルートは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次に、Service Broker ルートで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に一覧で示します。  
  
|Service Broker ルート権限|権限が含まれる Service Broker ルート権限|権限が含まれるデータベース権限|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Service Broker サービス  
 Service Broker サービスは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次に、Service Broker サービスで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に一覧で示します。  
  
|Service Broker サービス権限|権限が含まれる Service Broker サービス権限|権限が含まれるデータベース権限|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>権限  
 権限の許可者 (または AS オプションで指定されたプリンシパル) は、GRANT OPTION によって与えられた権限を保持しているか、権限が暗黙的に与えられる上位の権限を保持している必要があります。  
  
 AS オプションを使用する場合は、次の追加要件があります。  
  
|AS *granting_principal*|必要な追加権限|  
|------------------------------|------------------------------------|  
|データベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|Windows ログインにマップされているデータベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|Windows グループにマップされているデータベース ユーザー|メンバーシップである Windows グループのメンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|証明書にマップされているデータベース ユーザー|メンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|非対称キーにマップされるデータベース ユーザー|メンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|任意のサーバー プリンシパルにマップされていないデータベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|データベース ロール|メンバーシップ、ロールに対する ALTER 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|アプリケーション ロール|メンバーシップ、ロールに対する ALTER 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
  
 オブジェクトの所有者は、所有するオブジェクトの権限を許可できます。 セキュリティ保護可能なリソースに対して CONTROL 権限があるプリンシパルは、そのリソースの権限を許可できます。  
  
 メンバーなど、CONTROL SERVER 権限の付与、 **sysadmin**固定サーバー ロールは、いずれかに対する権限を許可できるサーバーのセキュリティ保護可能な。 メンバーなど、データベースに対する CONTROL 権限の付与、 **db_owner**固定データベース ロールがいずれかに対する権限を許可できるデータベースのセキュリティ保護可能な。 スキーマに対する CONTROL 権限が許可されているユーザーは、スキーマ内のオブジェクトに対する権限を許可できます。  
  
## <a name="see-also"></a>参照  
 [SQL Server Service Broker (SQL Server Service Broker)](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
