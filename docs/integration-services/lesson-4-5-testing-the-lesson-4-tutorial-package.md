---
title: "手順 5: レッスン 4 のチュートリアル パッケージのテスト | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 97ea428e44a7d7efc773653837b14f20efb424f8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="lesson-4-5---testing-the-lesson-4-tutorial-package"></a>レッスン 4-5 - レッスン 4 のチュートリアル パッケージのテスト
壊れているファイル Currency_BAD.txt を実行すると、CurrencyKey 参照変換の照合結果の生成に失敗します。 ただし、CurrencyKey 参照変換のエラー出力は、失敗した行を新しい [Failed Rows] 変換先へリダイレクトするように構成されています。したがって、コンポーネント自体は失敗せず、パッケージは正常に実行されます。 エラーがある行はすべて、ErrorOutput.txt に書き込まれます。  
  
この実習では、パッケージを実行して、変更したエラー出力構成をテストします。 パッケージが正常に実行されたら、ErrorOutput.txt ファイルの内容を確認します。  
  
> [!NOTE]  
> ErrorOutput.txt ファイルにエラー行が蓄積されないようにする場合は、パッケージ実行の間に手動でファイルの内容を削除してください。  
  
## <a name="checking-the-package-layout"></a>パッケージ レイアウトの確認  
パッケージをテストする前に、次の図に示すオブジェクトがレッスン 4 のパッケージの制御フローとデータ フローに含まれていることを確認します。 制御フローはレッスン 2 ～ 4 の制御フローと同じである必要があります。  
  
**制御フロー**  
  
![パッケージ内の制御フロー](../integration-services/media/task4lesson2control.gif "パッケージ内の制御フロー")  
  
**データ フロー**  
  
![パッケージ内のデータ フロー](../integration-services/media/task5lesson5data.gif "パッケージ内のデータ フロー")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>レッスン 4 のチュートリアル パッケージを実行するには  
  
1.  **[デバッグ]** メニューの **[デバッグの開始]**をクリックします。  
  
2.  パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]**をクリックします。  
  
### <a name="to-verify-the-contents-of-the-erroroutputtxt-file"></a>ErrorOutput.txt ファイルの内容を確認するには  
  
-   メモ帳などのテキスト エディターで ErrorOutput.txt ファイルを開きます。 既定の列の順序は、AverageRate、CurrencyID、CurrencyDate、EndOfDateRate、ErrorCode、ErrorColumn、ErrorDescription です。  
  
    ファイルのすべての行には、一致しない CurrencyID 値 BAD、ErrorCode 値 -1071607778、ErrorColumn 値 0、ErrorDescription 値 "参照中に一致する行が見つかりませんでした" が含まれています。 エラーは列固有ではなく、ErrorColumn の値は 0 になっています。 これは失敗した参照操作を表します。 のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。  
  
  
  
