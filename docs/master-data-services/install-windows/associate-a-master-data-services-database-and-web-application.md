---
title: "Master Data Services データベースと Web アプリケーションの関連付け | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccb25672-f71d-4135-b548-f50eb45d8fa5
caps.latest.revision: 9
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 31a1db8384143ead4a5d8adc81a8b905129d6b4e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="associate-a-master-data-services-database-and-web-application"></a>Master Data Services データベースと Web アプリケーションの関連付け
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションを [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースに関連付け、Web 操作に使用するデータベースを指定します。  
  
## <a name="prerequisites"></a>前提条件  
  
-   [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] がローカル コンピューターにインストールされている必要があります。 詳細については、「 [マスター データ サービスのインストール](../../master-data-services/install-windows/install-master-data-services.md)」を参照してください。  
  
-   ローカルの [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションが存在している必要があります。 詳細については、「[マスター データ マネージャー Web アプリケーションを作成する方法 &#40;マスター データ サービス&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)」を参照してください。  
  
-   ローカルまたはリモートの [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースのどちらかが存在している必要があります。 詳細については、「 [マスター データ サービス データベースの作成](../../master-data-services/install-windows/create-a-master-data-services-database.md)」をご覧ください。  
  
### <a name="to-associate-a-master-data-services-database-and-web-application"></a>Master Data Services データベースと Web アプリケーションを関連付けるには  
  
1.  [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]を開きます。  
  
2.  左ペインで **[Web の構成]**をクリックします。  
  
3.  **[Web の構成]** ページで、 **[Web アプリケーション]**の下の **[Web サイト]** ボックスの一覧から [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションを含む Web サイトを選択します。  
  
4.  **[Web アプリケーション]** ボックスで、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]をホストする Web アプリケーションを選択します。  
  
5.  **[アプリケーションとデータベースの関連付け]**で、 **[選択]**をクリックします。 **[データベースへの接続]** ダイアログ ボックスが開きます。  
  
6.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースをホストする [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] のインスタンスの接続情報を指定し、 **[接続]**をクリックします。  
  
7.  **[Master Data Services データベース]** ボックスの一覧から、Web アプリケーションに関連付けるデータベースを選択し、 **[OK]**をクリックします。  
  
8.  **[アプリケーションとデータベースの関連付け]**で、インスタンスおよびデータベースの情報が正しいことを確認し、 **[適用]**をクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   Web アプリケーションが作成されると、プログラムによる [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サービスへのアクセスが自動的に有効になります。 開発者がサービス メタデータにアクセスし、プログラムからプロキシ クラスを簡単に生成するには、メタデータ パブリッシュを有効にします。 詳細については、「 [マスター データ マネージャー Web サービス プロキシ クラスの作成](../../master-data-services/develop/create-master-data-manager-web-service-proxy-classes.md)」を参照してください。  
  
-   ユーザーおよびグループを [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]に追加します。 どのユーザーまたはグループも [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] へのアクセス権が付与されていない場合は、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] システム管理者の資格情報を使用して、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] を開く必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../../master-data-services/administrators-master-data-services.md)」および「[Users and Groups &#40;Master Data Services&#41; (ユーザーおよびグループ &#40;Master Data Services&#41;)](../../master-data-services/users-and-groups-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [マスター データ サービスのインストール](../../master-data-services/install-windows/install-master-data-services.md)   
 [[Web の構成] ページ &#40;マスター データ サービス構成マネージャー&#41;](../../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
  