---
title: "インストール先の指定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining - "setup-install"
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1d17bf0953012ef95537bd3649c06cceda344db1
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="deployment-script-files---specifying-the-installation-target"></a>配置スクリプト ファイルのインストール先の指定
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]配置ウィザードからインストール先の情報を読み取り、 \<*プロジェクト名*> >.deploymenttargets ファイル。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ビルドするときに、このファイルを作成、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースとで指定したサーバーを使用して、**展開**のページ、 *\<プロジェクト名 >* **プロパティ ページ**を作成するダイアログボックス\<*プロジェクト名*> .targets ファイル。  
  
## <a name="modifying-the-installation-target-for-deployment"></a>配置に関するインストール先の変更  
 場合によっては、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [配置] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ページで指定されたものとは別のデータベースまたは **インスタンスに** プロジェクトを配置する必要が生じることがあります。 たとえば、配置前のテストを行うためにプロジェクトをサーバーに配置し、テストの完了後にそのプロジェクトを実稼働サーバーに配置する必要が生じることがあります。 また、完成したテスト済みのプロジェクトをネットワーク負荷分散クラスター内の複数の実稼働サーバーに配置するか、ステージング サーバーおよび実稼働サーバーに配置する必要が生じることもあります。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを別のデータベースまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに配置するには、次の手順で説明するいずれかの方法に従って、入力ファイル内のインストール先を変更します。  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a>入力ファイルの生成後にインストール先を変更するには  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行します。 **[インストールの対象]** ページで、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスとデータベースの新しいインストール先を指定します。  
  
     — または —  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。 応答ファイル モードの詳細については、「 [Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)」を参照してください。  
  
     または  
  
-   変更、 \<*プロジェクト名*> 任意のテキスト エディターを使用して、>.deploymenttargets ファイル。  
  
## <a name="see-also"></a>参照  
 [パーティションおよびロールの配置オプションを指定します。](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)   
 [ソリューションの配置の構成設定の指定](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)   
 [処理オプションの指定](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
  
