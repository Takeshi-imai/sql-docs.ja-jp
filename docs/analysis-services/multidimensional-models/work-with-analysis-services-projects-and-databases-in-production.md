---
title: "扱う Analysis Services プロジェクトおよび実稼働環境でデータベース |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Analysis Services, projects
ms.assetid: c589097f-ad29-4b97-8c7e-b8a910909c1a
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af715c072f35ebee79a126eed58308d1b1f27629
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="work-with-analysis-services-projects-and-databases-in-production"></a>扱う Analysis Services プロジェクトおよび実稼働環境でのデータベース
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]開発し、展開した後、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]からデータベース、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクトを[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンス、配置済みデータベース内のオブジェクトを変更する方法を決定する必要があります。 セキュリティ ロール、パーティション分割、ストレージ設定などの変更は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のいずれかを使用して行うことができます。 その他の変更 (属性やユーザー定義階層の追加など) を行うには、プロジェクト モードまたはオンライン モードで [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を実行する必要があります。  
  
 オンライン モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、配置した [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースに変更を加えると、その直後に、配置で使用された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトは期限切れになります。 開発担当者が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト内で変更を加え、変更したプロジェクトを配置しようとすると、データベース全体を上書きするように求めるメッセージが表示されます。 データベース全体を上書きする場合は、データベースの処理も必要になります。 配置されたデータベースを実稼働環境のスタッフが直接変更した場合は、その変更を開発チームに通知しておかないと、この問題は複雑になります。それは、開発チーム側が、自分たちが変更した内容が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに反映されていない理由を知らされないままとなるからです。  
  
 SQL Server の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ツールを使用すると、このような問題を未然に防ぐことができます。次の方法があります。  
  
-   方法 1 : [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの実稼働環境バージョンに変更を加えるたびに、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの変更バージョンに基づいて新しい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを作成します。 この新しい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトは、プロジェクトのマスター コピーとしてソース管理システムにチェックインできます。 この方法は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をオンライン モードで使用して [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースに変更を加えたかどうかに関係なく利用できます。  
  
-   方法 2 : [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をプロジェクト モードで使用することにより、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースの実稼働バージョンにのみ変更を加えます。 この方法では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の配置ウィザードで利用できるオプションを使用して、セキュリティ ロールやストレージ設定など、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で加えられた変更を維持できます。 たとえば、プロジェクト ファイル内のデザイン関連設定を維持 (ストレージ設定およびセキュリティ ロールを除外) し、オンライン サーバーのストレージ設定およびセキュリティ ロールが使用されるようにすることができます。  
  
-   方法 3 : [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をオンライン モードで使用することにより、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースの実稼働バージョンにのみ変更を加えます。 SQL Server Management Studio と Business Intelligence Development Studio のいずれのツールも、同じオンライン サーバーだけを操作するので、バージョンが異なってもデータベースの同期が外れる可能性はありません。  
  
  
