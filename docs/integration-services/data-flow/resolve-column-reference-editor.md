---
title: "列参照解決エディター | Microsoft Docs"
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
- sql13.dts.designer.resolvereferences.preview.F1
- sql13.dts.designer.resolvereferences.mapper.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8375025851be1382ab34cfc492be88472577c05
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="resolve-column-reference-editor"></a>列参照解決エディター
  入力パスが接続されていない場合、またはパスにマップ解除された列が存在する場合、対応するデータ パスの横にエラー アイコンが表示されます。 列参照エラーの解決を簡素化するために、参照の解決エディターを使用して、マップ解除された出力列を、実行ツリーのすべてのパスのマップ解除された入力列とリンクできます。 また、参照の解決エディターでは、解決されているパスを示すためにパスが強調表示されます。  
  
> [!NOTE]  
>  入力パスが接続されていない場合でもコンポーネントを編集できます。  
  
 すべての列参照が解決された後、他のデータ パス エラーが存在しなければ、データ パスの横にエラー アイコンが表示されなくなります。  
  
## <a name="options"></a>および  
 **マップ解除された出力列 (変換元)**    
 現在マップされていない上流パスの列。  
  
**マップされた列 (変換元)**    
 下流パスから列にマップされた上流パスの列。  
  
**マップされた列 (変換先)**    
 下流パスから列にマップされた上流パスの列。  
  
**マップ解除された入力列 (変換先)**    
 現在マップされていない下流パスの列。  
  
**[マップ解除された入力列の削除]**  
 [マップ解除された入力列の削除] をオンにすると、データ パスの変換先でマップ解除された列が無視されます。 \[変更のプレビュー] ボタンには、[OK] ボタンを押したときに行われる変更の一覧が表示されます。  
  
  
