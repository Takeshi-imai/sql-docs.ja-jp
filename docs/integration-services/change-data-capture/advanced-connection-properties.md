---
title: "高度な接続プロパティ | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9076804e4a55c8f8e522ee8881b61be6f8191da0
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="advanced-connection-properties"></a>高度な接続プロパティ
  **[高度な接続プロパティ]** ダイアログ ボックスを使用すると、接続文字列に接続パラメーターをさらに追加できます。  
  
 追加の接続パラメーターには、使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース インスタンスでサポートされる任意の ODBC 接続パラメーターを使用できます。  
  
 **[高度な接続プロパティ]** ダイアログ ボックスを使用して追加したパラメーターは、 **[SQL Server への接続]** ダイアログ ボックスで選択したパラメーターに追加されます。  
  
 指定した各パラメーターの最後のインスタンスは、そのパラメーターの前のインスタンスよりも優先されます。 **[高度な接続パラメーター]** ダイアログ ボックスを使用して追加したパラメーターは、 **[SQL Server 接続]** ダイアログ ボックスで指定したパラメーターの後に続き、それらのパラメーターを置換します。 たとえば、 **[SQL Server 接続]** ダイアログ ボックスの [サーバー名] で「SERVER1」と指定し、 **[追加の接続パラメーター]** ページで「;SERVER=SERVER2」と指定した場合、SERVER2 に接続されます。  
  
 **[高度な接続プロパティ]** ダイアログ ボックスを使用して追加したパラメーターは、プレーンテキストとして渡されます。  
  
> [!IMPORTANT]  
>  **[高度な接続プロパティ]** ダイアログ ボックスにはログイン資格情報を含めないでください。 このダイアログ ボックスで指定したパラメーターは、ネットワーク経由で渡されるときに暗号化されません。  
  
## <a name="see-also"></a>参照  
 [CDC デザイナー コンソールへのアクセス](../../integration-services/change-data-capture/access-the-cdc-designer-console.md)   
 [インスタンスの作成のための SQL Server 接続](../../integration-services/change-data-capture/sql-server-connection-for-instance-creation.md)  
  
  
