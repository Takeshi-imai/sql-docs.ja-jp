---
title: "Reporting Services の拡張機能 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- SQL Server Reporting Services, extending
- extensions [Reporting Services], about extensions
- SSIS, extending
- Reporting Services, extending
- extensions [Reporting Services]
ms.assetid: 2bf17ae4-2292-4a58-a1f0-56e99abd9b69
caps.latest.revision: "45"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 05b06d0069440691f32f89e89536fa53ad9400b8
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="reporting-services-extensions"></a>Reporting Services の拡張機能
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のモジュール式アーキテクチャは、拡張性を考慮して設計されています。 マネージ コード API を使用して、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の多くのコンポーネントで使用される拡張機能を容易に開発、インストール、および管理できます。 プライベートまたは共有のアセンブリを [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を使用して作成し、変化するビジネス要件に応じて新しい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の機能を追加できます。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のユニークな拡張可能アーキテクチャによって、開発者は、製品とそのコンポーネントの特定の機能を拡張できます。 現在では、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ処理機能を拡張するために幅広いサポートがあります。 データ処理 API では、使い慣れた [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーのコンストラクトと規約が採用されているので、開発者は、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に新しいデータ処理を追加することができます。 これらのデータ処理拡張機能によって、レポート サーバーとレポート デザイナーの両方に機能を追加し、カスタム データをレポートにシームレスに統合できます。  
  
 配信拡張機能もサポートされています。 配信 API は [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] アーキテクチャと完全に統合されているので、さまざまな配信メカニズムを使用して、レポート通知をユーザーに送信できます。 レポート サーバーを拡張してカスタム配信をユーザーに提供できます。レポート マネージャーのサブスクリプション管理ページを拡張して、カスタム配信拡張機能を使用したサブスクリプションを可能にします。  
  
 別のレポート サーバー拡張機能であるレポート定義カスタマイズ拡張機能 (RDCE) では、レポート定義を処理エンジンに渡す前に動的にカスタマイズできます。 レポートは、ユーザーや言語などの要因に基づいてカスタマイズできます。 たとえば、部署のマネージャーやメンバーなどのユーザーごとに異なるビューを実装したり、フランス語やアラビア語では異なるレイアウトで表示されるようにレポートをカスタマイズしたりできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [拡張機能のセキュリティに関する考慮事項](../../reporting-services/extensions/security-considerations-for-extensions.md)  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 拡張機能の開発と配置に関連するセキュリティ上の問題について説明します。  
  
 [データ処理拡張機能の実装](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ処理拡張機能を実装するための要件と手順について説明します。  
  
 [配信拡張機能の実装](../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の配信拡張機能を実装するための要件と手順について説明します。  
  
 [表示拡張機能の実装](../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)  
 表示拡張機能の開発の概要が記載されています。  
  
 [セキュリティ拡張機能の実装](../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のセキュリティ拡張機能を実装するための要件と手順について説明します。  
  
 [Reporting Services 拡張機能ライブラリ](../../reporting-services/extensions/reporting-services-extension-library.md)  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の拡張可能な機能を対象とした拡張機能 API ライブラリのプログラミング リファレンスです。  
  
  
