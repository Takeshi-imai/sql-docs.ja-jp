---
title: "データベース ログイン、ユーザー、およびロール (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Master Data Services], database roles
- database [Master Data Services], users
- security [Master Data Services], database users
- database [Master Data Services], roles
- database [Master Data Services], logins
- security [Master Data Services], database logins
ms.assetid: 72ee383e-a619-461b-9f9d-1cac162ab0c5
caps.latest.revision: 9
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: dc95616efefbe35dc835accc377743451556288e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="database-logins-users-and-roles-master-data-services"></a>データベース ログイン、ユーザー、およびロール (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] には、 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] データベースをホストする [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] インスタンスに自動的にインストールされるログイン、ユーザー、およびロールがあります。 これらのログイン、ユーザー、およびロールは変更しないでください。  
  
## <a name="logins"></a>ログイン  
  
|Login|Description|  
|-----------|-----------------|  
|**mds_dlp_login**|UNSAFE アセンブリを作成できます。 詳細については、「 [アセンブリの作成](../relational-databases/clr-integration/assemblies/creating-an-assembly.md)」を参照してください。<br /><br /> - ランダムに生成されたパスワードでのログインは無効です。<br /><br /> - [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの場合は、dbo にマップされます。<br /><br /> - msdb の場合は、mds_clr_user がこのログインにマップされます。|  
|**mds_email_login**|通知に使用されるログインは有効です。<br /><br /> msdb および [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの場合は、mds_email_user がこのログインにマップされます。|  
  
## <a name="msdb-users"></a>msdb ユーザー  
  
|ユーザー|Description|  
|----------|-----------------|  
|**mds_clr_user**|使用されていません。 mds_dlp_login にマップされます。|  
|**mds_email_user**|通知に使用します。<br /><br /> - mds_email_login にマップされます。<br /><br /> - DatabaseMailUserRole ロールのメンバーです。|  
  
## <a name="master-data-services-database-users"></a>マスター データ サービス データベース ユーザー  
  
|ユーザー|Description|  
|----------|-----------------|  
|**mds_email_user**|通知に使用します。<br /><br /> - mdm スキーマに対する SELECT 権限があります。<br /><br /> - mdm.MemberGetCriteria ユーザー定義テーブル型に対する EXECUTE 権限があります。<br /><br /> - mdm.udpNotificationQueueActivate ストアド プロシージャに対する EXECUTE 権限があります。|  
|**mds_schema_user**|mdm スキーマと mdq スキーマを所有します。 既定のスキーマは mdm です。<br /><br /> ログインはマップされません。|  
|**mds_ssb_user**|Service Broker タスクを実行するために使用します。<br /><br /> - すべてのスキーマに対する DELETE、INSERT、REFERENCES、SELECT、および UPDATE 権限があります。<br /><br /> - ログインはマップされません。|  
  
## <a name="master-data-services-database-role"></a>マスター データ サービス データベース ロール  
  
|ロール|Description|Permissions|  
|----------|-----------------|-----------------|  
|**mds_exec**|このロールには、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] Web アプリケーションを作成してアプリケーション プールのアカウントを指定したときに [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] で指定したアカウントが含まれます。|すべてのスキーマに対する EXECUTE 権限<br /><br /> <br /><br /> 次のテーブルに対する ALTER、INSERT、および SELECT 権限<br /><br /> mdm.tblStgMember<br /><br /> mdm.tblStgMemberAttribute<br /><br /> mdm.tbleStgRelationship<br /><br /> <br /><br /> 次のテーブルに対する SELECT 権限<br /><br /> mdm.tblUser<br /><br /> mdm.tblUserGroup<br /><br /> mdm.tblUserPreference<br /><br /> <br /><br /> 次のビューに対する SELECT 権限<br /><br /> mdm.viw_SYSTEM_SECURITY_NAVIGATION<br /><br /> mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL<br /><br /> mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL_MEMBER<br /><br /> mdm.viw_SYSTEM_SECURITY_USER_MODEL|  
  
## <a name="schemas"></a>スキーマ  
  
|ロール|Description|  
|----------|-----------------|  
|**mdm**|mdq スキーマに含まれている関数以外のすべての [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース オブジェクトおよび Service Broker オブジェクトが含まれます。|  
|**mdq**|正規表現または類似性に基づくメンバーの結果のフィルター処理や書式設定通知電子メールに関連する [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース関数が含まれます。|  
|**stg**|ステージング処理に関連する [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース テーブル、ストアド プロシージャ、およびビューが含まれます。 これらのオブジェクトは削除しないでください。 ステージング処理の詳細については、「[概要: テーブルからのデータのインポート (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [データベース オブジェクト セキュリティ (マスター データ サービス)](../master-data-services/database-object-security-master-data-services.md)  
  
  