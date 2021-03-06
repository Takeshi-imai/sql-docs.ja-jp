---
title: "ヒット カウントの指定 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.breakpt.hitcount
helpviewer_keywords:
- Transact-SQL debugger, breakpoint hit count
ms.assetid: 24836939-94ed-4e57-aa85-5d6938d859e4
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1430ec114f5aa14457fcff1d58a7f41e2e5bbe48
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="specify-a-hit-count"></a>ヒット カウントの指定
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] ブレークポイントのヒット カウントは、ブレークポイントに達するたびに [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーによって増加されるカウンターです。 指定したヒット カウントに達し、指定したブレークポイントの条件が満たされると、ブレークポイントに指定されたアクションがデバッガーによって実行されます。  
  
## <a name="hit-count-considerations"></a>ヒット カウントの考慮事項  
 既定では、ブレークポイントにヒットするたびに、実行が中断します。 次のオプションのいずれかを選択できます。  
  
-   常に中断する (既定)。  
  
-   ヒット カウントが指定した値と等しくなったときに中断する。  
  
-   ヒット カウントが指定した値の倍数と等しくなったときに中断する。  
  
-   ヒット カウントが指定した値以上になったときに中断する。  
  
 ブレークポイントのヒット カウントは、デバッグ セッションのスコープ内で増加します。 すべてのヒット カウントは各デバッグ セッションの開始時に 0 に設定されます。  
  
 ブレークポイントで実行を中断せずに、ブレークポイントにヒットした回数を追跡する場合は、ヒット カウントに非常に大きい値を指定して、ブレークポイントで中断しないようにします。  
  
 ブレークポイントの既定のアクションでは、ヒット カウントとブレークポイントの条件の両方が満たされたときに、実行が中断されます。 他のアクションを指定する方法の詳細については、「 [ブレークポイント アクションの指定](../../relational-databases/scripting/specify-a-breakpoint-action.md)」を参照してください。  
  
#### <a name="to-specify-a-hit-count"></a>ヒット カウントを指定するには  
  
1.  エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。  
  
     - または -  
  
     **[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。  
  
2.  **[ブレークポイントのヒット カウント]** ダイアログ ボックスで、 **[ブレークポイントをヒットした時]** ボックスから目的の動作を選択します。  
  
     **[常に中断]**以外の設定を選択すると、一覧の右側にテキスト ボックスが表示されます。 テキスト ボックスに整数を入力して、目的のヒット カウントを指定します。  
  
3.  **[OK]** をクリックして変更を適用するか、 **[キャンセル]** をクリックして変更を適用せずに終了します。  
  
#### <a name="to-view-or-reset-the-current-hit-count"></a>現在のヒット カウントを表示またはリセットするには  
  
1.  エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。  
  
     - または -  
  
     **[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。  
  
2.  **[ブレークポイントのヒット カウント]** ダイアログ ボックスの **[リセット]** ボタンのすぐ上に、 **[現在のヒット カウント]** が表示されます。  
  
3.  現在のヒット カウントを 0 に設定する場合は、 **[リセット]** をクリックします。  
  
4.  **[OK]** または **[キャンセル]** をクリックして、ダイアログ ボックスを終了します。  
  
## <a name="see-also"></a>参照  
 [ブレークポイント条件の指定](../../relational-databases/scripting/specify-a-breakpoint-condition.md)  
  
  
