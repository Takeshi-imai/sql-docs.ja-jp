---
title: "ナレッジ ベースの作成 | Microsoft Docs"
ms.custom: 
ms.date: 07/31/2012
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51eff161-6ecd-4ee4-8187-1dd8ef4814bd
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8fe15c5c9313fee10edbd7a9ebc3fd282dafa5f8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="building-a-knowledge-base"></a>ナレッジ ベースの作成
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のナレッジ ベースはデータに関するナレッジのリポジトリです。ナレッジ ベースを使用して、データを理解し、その整合性を維持できます。 ナレッジ ベースはドメインで構成され、各ドメインはデータ フィールド内のデータを表します。 ナレッジ ベースは、DQS でデータベース上のデータのクレンジングと重複除去を実行するのに使用されます。 データ クレンジング用にナレッジ ベースを準備するには、データ サンプルのコンピューター支援型分析を実行し、ドメインの値を対話形式で管理します。 DQS を使用して、ナレッジのインポート、ルールおよび関係の作成、データ値の直接変更、既定のデータベースの利用を行うことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 ナレッジ ベースで次の操作を実行できます。  
  
|||  
|-|-|  
|ナレッジ ベースを既存のナレッジ ベースまたは .dqs データ ファイルから新規に作成します。|[ナレッジ ベースを作成する](../data-quality-services/create-a-knowledge-base.md)|  
|既存のナレッジ ベースを開き、ナレッジ検出やドメイン管理の実行、または照合ポリシーの追加を行います。|[ナレッジ ベースを開く](../data-quality-services/open-a-knowledge-base.md)|  
|ナレッジ ベースでの管理操作 (ナレッジ ベースを開く、ナレッジ ベースのロックの解除、ナレッジ ベースでの作業内容の破棄、ナレッジ ベース名の変更、ナレッジ ベースの削除、ナレッジ ベースのプロパティの表示など) を実行します。|[ナレッジ ベースを管理する](../data-quality-services/manage-a-knowledge-base.md)|  
|ナレッジ検出を通じたナレッジ ベースへのナレッジの追加、ドメイン値の管理、照合ポリシーの追加、ナレッジ、ドメイン、値のインポート、または既定のナレッジ ベースの DQS データの使用を行います。|[ナレッジ ベースにナレッジを追加する](../data-quality-services/adding-knowledge-to-a-knowledge-base.md)|  
|データ品質基準のデータ サンプルを分析します。|[ナレッジ検出を実行する](../data-quality-services/perform-knowledge-discovery.md)|  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|ナレッジをナレッジ ベースにインポートするか、ナレッジ ベースからナレッジをエクスポートします。|[ナレッジのインポートとエクスポート](../data-quality-services/importing-and-exporting-knowledge.md)|  
|単一ドメインを作成し、ナレッジをドメインに追加します。|[ドメインの管理](../data-quality-services/managing-a-domain.md)|  
|複合ドメインを作成し、ナレッジをドメインに追加します。|[複合ドメインの管理](../data-quality-services/managing-a-composite-domain.md)|  
  
  