---
title: "1 台のコンピューターでの SSIS Scale Out の概要 | Microsoft Docs"
ms.description: This article shows you everything you need to know to get started with SSIS Scale Out on a single computer
ms.custom: 
ms.date: 12/13/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: douglasl
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ed813ca6ea9775c6aeb3c40dac63d7ec5b630ee5
ms.sourcegitcommit: 4dab7c60fb66d61074057eb1cee73f9b24751a8f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2017
---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>1 台のコンピューターでの Integration Services (SSIS) Scale Out の概要
このセクションでは、コンピューターが 1 台の環境で Integration Services Scale Out を設定する方法を紹介します。既定の設定を利用します。

## <a name="1-install-sql-server-features"></a>1.SQL Server 機能のインストール
SQL Server インストール ウィザードの **[機能の選択]** ページで、次の項目を選択します。
-   データベース エンジン サービス
-   Integration Services
    -   Scale Out Master
    -   Scale Out Worker

![機能の選択、一覧の前半部分](media/feature-select-onebox1.PNG)

![機能の選択、一覧の後半部分](media/feature-select-onebox2.PNG)

**[サーバー構成]** ページで、**[次へ]** をクリックし、既定のサービス アカウントとスタートアップの種類を受け入れます。

**[データベース エンジンの構成]** ページで、**[混合モード]** を選択し、**[現在のユーザーの追加]** をクリックします。 

![エンジンの構成](media/engine-config.PNG)

**[Integration Services Scale Out の構成 - マスター ノード]** ページと **[Integration Services Scale Out の構成 - ワーカーノード]** ページで、**[次へ]** をクリックし、ポートと証明書の既定の設定を受け入れます。

SQL Server のインストール ウィザードを完了します。

## <a name="2-install-sql-server-management-studio"></a>2.SQL Server Management Studio のインストール

[SQL Server Management Studio (SSMS) ダウンロードしてインストールします](../../ssms/download-sql-server-management-studio-ssms.md)。

## <a name="3-enable-scale-out"></a>3.スケール アウトの有効化
SSMS を開き、ローカル Sql Server インスタンスに接続します。
オブジェクト エクスプローラーで **[Integration Services カタログ]** を右クリックし、**[カタログの作成]** を選択します。

**[カタログの作成]** ダイアログで、**[SSIS スケール アウト マスターとしてこのサーバーを有効にする]** オプションが既定で選択されています。

## <a name="4-enable-a-scale-out-worker"></a>4.Scale Out Worker の有効化
SSMS で **[SSISDB]** を右クリックし、**[スケール アウトの管理]** を選択します。 

![スケール アウトの管理](media/manage-scale-out.PNG)

Integration Services Scale Out Manager アプリが開きます。 詳細については、[Scale Out Manager](integration-services-ssis-scale-out-manager.md) に関するページを参照してください。

Scale Out Worker を有効にするには、**[ワーカー マネージャー]** に切り替え、有効にするワーカーを選択します。 ワーカーは既定では無効にされます。 **[ワーカーの有効化]** をクリックして、選択したワーカーを有効にします。

## <a name="5-run-packages-in-scale-out"></a>5.Scale Out でのパッケージの実行
これで、Scale Out で SSIS パッケージを実行する準備が整いました。詳細については、「[Integration Services (SSIS) Scale Out でパッケージを実行する](run-packages-in-integration-services-ssis-scale-out.md)」を参照してください。

## <a name="next-steps"></a>次の手順
-   [Scale Out Manager による Scale Out Worker の追加](add-scale-out-worker.md)
