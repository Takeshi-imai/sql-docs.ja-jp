---
title: "列インポート変換 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.importcolumntrans.f1
helpviewer_keywords:
- Import Column transformation [Integration Services]
- columns [Integration Services], importing
- importing data, SSIS packages
- inserting data
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1d8884e76a081e329ec971c253443a32f93efc90
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="import-column-transformation"></a>列インポート変換
  列インポート変換は、ファイルのデータを読み取り、そのデータをデータ フローの列に追加します。 この変換を使用すると、パッケージは、別々のファイルに格納されているテキストや画像を 1 つのデータ フローに追加できます。 たとえば、製品情報を保存するテーブルにデータを読み込むデータ フローに列インポート変換を含めると、各製品に対する顧客評価をファイルからインポートし、データ フローに追加できます。  
  
 列インポート変換は、次の方法で構成できます。  
  
-   データを追加する列を指定します。  
  
-   バイト順マーク (BOM) が必要かどうかを指定します。  
  
    > [!NOTE]  
    >  BOM が必要になるのは、データが DT_NTEXT データ型の場合だけです。  
  
 変換入力の列には、データを保持するファイル名が含まれます。 データセットの各行には、異なるファイルを指定できます。 列インポート変換が行を処理すると、ファイル名を読み取り、ファイル システム内の対応するファイルを開き、ファイルの内容を出力列に読み込みます。 出力列のデータ型は、DT_TEXT、DT_NTEXT、または DT_IMAGE 型である必要があります。 詳細については、「 [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
 この変換は、1 つの入力、1 つの出力、および 1 つのエラー出力をとります。  
  
## <a name="configuration-of-the-import-column-transformation"></a>列インポート変換の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 このコンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [列エクスポート変換](../../../integration-services/data-flow/transformations/export-column-transformation.md)   
 [データ フロー](../../../integration-services/data-flow/data-flow.md)   
 [Integration Services の変換](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
