---
title: "列参照解決エディター |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.resolvereferences.preview.F1
- sql13.dts.designer.resolvereferences.mapper.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f2ff8a97d45d75c3e93d4aa3111b653c9612b889
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="resolve-column-reference-editor"></a>列参照解決エディター
  入力パスが接続されていない場合、またはパスにマップ解除された列が存在する場合、対応するデータ パスの横にエラー アイコンが表示されます。 列参照エラーの解決を簡略化は、参照解決エディターを使用すると、実行ツリーのすべてのパスをマップ解除された入力列をマップ解除された出力列をリンクできます。 また、参照の解決エディターでは、解決されているパスを示すためにパスが強調表示されます。  
  
> [!NOTE]  
>  その入力パスが接続されていない場合でもコンポーネントを編集することは  
  
 すべての列参照が解決された後、他のデータ パス エラーが存在しなければ、データ パスの横にエラー アイコンが表示されなくなります。  
  
## <a name="options"></a>オプション  
 **マップ解除された出力列 (変換元)**    
 現在マップされていない上流パスの列。  
  
**マップされた列 (変換元)**    
 下流パスから列にマップされた上流パスの列。  
  
**マップされた列 (変換先)**    
 下流パスから列にマップされた上流パスの列。  
  
**マップされていない入力列 (変換先)**    
 現在マップされていない下流パスの列。  
  
**[マップ解除された入力列の削除]**  
 [マップ解除された入力列の削除] をオンにすると、データ パスの変換先でマップ解除された列が無視されます。 \[変更のプレビュー] ボタンには、[OK] ボタンを押したときに行われる変更の一覧が表示されます。  
  
  