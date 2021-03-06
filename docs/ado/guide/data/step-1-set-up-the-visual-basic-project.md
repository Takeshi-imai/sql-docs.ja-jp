---
title: "手順 1: Visual Basic プロジェクトの設定 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77d3bfa5-fc9f-4a72-93b4-790c7d227988
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ca52a0c56d37a8ebb5da2ef52cd98d71fa3f937d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="step-1-set-up-the-visual-basic-project"></a>手順 1: Visual Basic プロジェクトの設定します。
このシナリオである Microsoft Visual Basic 6.0、ADO 2.5 以降、Microsoft OLE DB Provider for Internet Publishing がシステムにインストールされていると見なされます。 まず、新しいプロジェクトを作成して、プロジェクトで既定のフォームに一部のコントロールを追加します。  
  
### <a name="to-create-an-ado-project"></a>ADO プロジェクトを作成するには  
  
1.  Microsoft Visual Basic では、新しい標準 EXE プロジェクトを作成します。  
  
2.  [プロジェクト] メニューからの参照を選択します。  
  
3.  "Microsoft ActiveX データ オブジェクト 2.5 Library"を選択し、[ok] をクリックします。  
  
### <a name="to-insert-controls-on-the-main-form"></a>メイン フォームにコントロールを挿入します。  
  
1.  Form1 にリスト ボックス コントロールを追加します。 名前プロパティを設定**lstMain**です。  
  
2.  Form1 にもう 1 つの ListBox コントロールを追加します。 名前プロパティを設定**lstDetails**です。  
  
3.  Form1 にテキスト ボックス コントロールを追加します。 名前プロパティを設定**txtDetails**です。  
  
## <a name="see-also"></a>参照  
 [インターネット発行シナリオ](../../../ado/guide/data/internet-publishing-scenario.md)   
 [手順 2: Main リスト ボックスを初期化する](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)
