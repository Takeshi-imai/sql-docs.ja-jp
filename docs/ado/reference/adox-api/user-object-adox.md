---
title: "ユーザー オブジェクト (ADOX) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- User
helpviewer_keywords:
- User object [ADOX]
ms.assetid: f68e32ce-ef7c-407d-bdb5-d280947ae0e2
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 70271f780557a7ad63df504f50962e88113348b1
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="user-object-adox"></a>ユーザー オブジェクト (ADOX)
セキュリティで保護されたデータベース内でのアクセス許可を持つユーザー アカウントを表します。  
  
## <a name="remarks"></a>解説  
 [ユーザー](../../../ado/reference/adox-api/users-collection-adox.md)のコレクション、[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)カタログのすべてのユーザーを表します。 **ユーザー**のコレクション、[グループ](../../../ado/reference/adox-api/group-object-adox.md)特定のグループのユーザーのみを表します。  
  
 プロパティ、コレクション、方法と、**ユーザー**オブジェクトをすることができます。  
  
-   使用して、ユーザーを識別、[名前](../../../ado/reference/adox-api/name-property-adox.md)プロパティです。  
  
-   持つユーザーのパスワードを変更、 [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md)メソッドです。  
  
-   ユーザーが読み取りになっているかどうかを判断書き込み、またはを使用した権限の削除、 [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md)と[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)メソッドです。  
  
-   アクセスと、ユーザーが所属するグループ、[グループ](../../../ado/reference/adox-api/groups-collection-adox.md)コレクション。  
  
-   プロバイダーに固有のプロパティへのアクセス、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
-   確認、 [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md)ユーザー。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [User オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [GetPermissions と SetPermissions メソッドの例 (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [グループのコレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
