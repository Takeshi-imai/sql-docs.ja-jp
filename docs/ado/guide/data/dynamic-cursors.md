---
title: "動的カーソル |Microsoft ドキュメント"
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
helpviewer_keywords:
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dbeb8f40cf6d1ad91a59fa9719410f26386953d4
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="dynamic-cursors"></a>動的カーソル
動的カーソルは、内部カーソルまたはカーソルの外部には、他のユーザーによってから、変更が発生するかどうかに関係なく、結果セット内の行に行われたすべての変更を検出します。 すべての insert、update、および delete ステートメントのすべてのユーザーによって行われた、カーソル内で表示されます。 動的カーソルは、行、順序、および、カーソルが開かれた後に結果セット内の値に加えられた変更を検出できます。 (ただし、カーソルのトランザクション分離レベルを「コミットされていない」設定すると) にコミットされるまで、カーソル外部から行った更新は表示されません。  
  
 たとえば、動的カーソル別のアプリケーションでは、2 つの行をフェッチそれらの行のいずれかを更新し、もう一方を削除します。 動的カーソルは、それらの行をフェッチするように場合、削除された行は見つかりませんが、更新された行の新しい値が表示されます。  
  
 動的カーソルは、適切な選択、アプリケーションはすべて同時に他のユーザーが行った更新を検出する必要があります。 使用して、 **adOpenDynamic CursorTypeEnum** ADO では動的カーソルを使用することを指定します。  
  
## <a name="see-also"></a>参照  
 [順方向専用カーソル](../../../ado/guide/data/forward-only-cursors.md)   
 [静的カーソル](../../../ado/guide/data/static-cursors.md)   
 [Keyset カーソル](../../../ado/guide/data/keyset-cursors.md)
