---
title: "カスタム ForEach 列挙子の開発 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-custom-objects
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom foreach enumerators [Integration Services]
- custom foreach enumerators [Integration Services], about custom foreach enumerators
- foreach enumerators [Integration Services]
ms.assetid: bffe26e0-1b9a-47ad-bae6-6b708cb4cf4f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 70fd72d198ff7f6ce5b7a79bbeed1a40f92c8aac
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="developing-a-custom-foreach-enumerator"></a>カスタム ForEach 列挙子の開発
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では、foreach 列挙子を使用して、コレクション内のアイテムを繰り返し処理したり、各要素に対して同じタスクを実行したりします。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] には、フォルダー内のすべてのファイル、データベース内のすべてのテーブル、パッケージ変数に格納された一覧のすべての要素など、最もよく使用されるコレクションをサポートする、さまざまな foreach 列挙子が含まれています。 提供される foreach 列挙子とコレクションが、要件を必ずしも満たさない場合は、カスタム foreach 列挙子を作成できます。  
  
 カスタム foreach 列挙子を作成するには、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> 基本クラスを継承するクラスを作成し、新しいクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 属性を適用し、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> メソッドなど、基本クラスの重要なメソッドとプロパティをオーバーライドする必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 ここでは、カスタム foreach 列挙子とそのカスタム ユーザー インターフェイスを作成、構成、およびコーディングする方法について説明します。  
  
 [カスタム Foreach 列挙子の作成](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/creating-a-custom-foreach-enumerator.md)  
 カスタム foreach 列挙子プロジェクト用のクラスの作成方法について説明します。  
  
 [カスタム Foreach 列挙子のコーディング](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/coding-a-custom-foreach-enumerator.md)  
 基本クラスのメソッドとプロパティのオーバーライドによる、カスタム foreach 列挙子の実装方法について説明します。  
  
 [カスタム ForEach 列挙子用ユーザー インターフェイスの開発](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
 ユーザー インターフェイス クラスと、カスタム foreach 列挙子の構成に使用するフォームの実装方法について説明します。  
  
## <a name="related-topics"></a>関連項目  
  
### <a name="information-common-to-all-custom-objects"></a>すべてのカスタム オブジェクトに共通の情報  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なカスタム オブジェクトのすべての種類に共通の情報については、次のトピックを参照してください。  
  
 [Integration Services 用のカスタム オブジェクトの開発](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のすべての型のカスタム オブジェクトを実装する基本手順について説明します。  
  
 [カスタム オブジェクトの永続化](../../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)  
 カスタムの永続性と、それが必要な場合について説明します。  
  
 [カスタム オブジェクトのビルド、配置、デバッグ](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 カスタム オブジェクトをビルド、署名、配置、およびデバッグする方法について説明します。  
  
### <a name="information-about-other-custom-objects"></a>その他のカスタム オブジェクトに関する情報  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なその他の種類のカスタム オブジェクトについては、次のトピックを参照してください。  
  
 [カスタム タスクの開発](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)  
 カスタム タスクのプログラム方法について説明します。  
  
 [カスタム接続マネージャーの開発](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 カスタム接続マネージャーのプログラム方法について説明します。  
  
 [カスタム ログ プロバイダーの開発](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 カスタム ログ プロバイダーのプログラム方法について説明します。  
  
 [カスタム データ フロー コンポーネントの開発](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)  
 カスタム データ フローの変換元、変換、変換先のプログラム方法について説明します。  
 
