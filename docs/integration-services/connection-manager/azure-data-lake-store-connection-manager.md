---
title: "Azure Data Lake Store 接続マネージャー | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: 
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9d98d6cf214a4d08e3a617ab19307bfd42b58189
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="azure-data-lake-store-connection-manager"></a>Azure Data Lake Store 接続マネージャー
SQL Server Integration Services (SSIS) パッケージでは、Azure Data Lake Store 接続マネージャーを使用して、次の 2 つの認証の種類のいずれかで Azure Data Lake Store サービスに接続できます。
-   Azure AD のユーザー ID
-   Azure AD のサービス ID 

Azure Data Lake Store 接続マネージャー は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。

>   [!NOTE]
> Azure Data Lake Store 接続マネージャーとこれを使用するコンポーネント (つまり、Azure Data Lake Store Source と Azure Data Lake Store Destination) がサービスに接続できるようにするために、必ず最新バージョンの Azure Feature Pack を [こちら](https://www.microsoft.com/download/details.aspx?id=49492)からダウンロードしてください。 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Azure Data Lake Store 接続マネージャーを構成する

1.  **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureDataLake]** を選択してから **[追加]** を選択します。 **[Azure Data Lake Store 接続マネージャー エディター]** ダイアログ ボックスが開きます。
  
2.  **[Azure Data Lake Store 接続マネージャー エディター]** ダイアログ ボックスの **[ADLS ホスト]** フィールドに、Azure Data Lake Store ホストの URL を入力します。 たとえば、`https://test.azuredatalakestore.net` や `test.azuredatalakestore.net` などです。
  
3.  **[認証]** フィールドで、Azure Data Lake Store のデータにアクセスするために適切な認証の種類を選択します。

    1.  **[Azure AD のユーザー ID]** 認証オプションを選択する場合は、次の操作を行います。
        1. **[ユーザー名]** と **[パスワード]** のフィールドに値を指定します。 
    
        2. 接続をテストするには、**[接続テスト]** を選択します。 自分自身またはテナント管理者が SSIS から Azure Data Lake Store データへのアクセスに同意していない場合は、プロンプトが表示されたときに **[同意する]** を選択します。 この同意エクスペリエンスの詳細については、「[Azure Active Directory とアプリケーションの統合](https://docs.microsoft.com/azure/active-directory/active-directory-integrating-applications#updating-an-application)」を参照してください。
    
        >   [!NOTE] 
        > **[Azure AD のユーザー ID]** 認証オプションを選択する場合、多要素認証と Microsoft アカウント認証はサポートされません。
    
    2. **[Azure AD のサービス ID]** 認証オプションを選択する場合は、次の操作を行います。
        1. Azure Data Lake データにアクセスするための Azure Active Directory (AAD) アプリケーションおよびサービス プリンシパルを作成します。
    
        2. 適切な権限を割り当てて、この AAD アプリケーションが Azure Data Lake リソースにアクセスできるようにします。 この認証オプションの詳細については、「[Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)」 (ポータルを使用して、リソースにアクセスできる Active Directory アプリケーションとサービス プリンシパルを作成する) を参照してください。
    
        3. **[クライアント ID]**、**[シークレット キー]** および **[テナント名]** の各フィールドに値を指定します。
    
        4. 接続をテストするには、**[接続テスト]** を選択します。  
  
6.  **[OK]** を選択して、**[Azure Data Lake Store 接続マネージャー エディター]** ダイアログ ボックスを閉じます。  

## <a name="view-the-properties-of-the-connection-manager"></a>接続マネージャーのプロパティを表示する
作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。  
  
  
