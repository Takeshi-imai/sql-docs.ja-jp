---
title: "Previous 関数 (レポート ビルダーおよび SSRS) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 9cbaa857daff88ffa155f29ff83c16d6d9a6b856
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="report-builder-functions---previous-function"></a>レポート ビルダーの関数の前の関数
  アイテムの、指定されたスコープ内の直前のインスタンスに対応する値または指定された集計値を返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *式 (expression)*  
 (**Variant** または **Binary**) データを識別し、直前の値を取得するための式 ( `Fields!Fieldname.Value` や `Sum(Fields!Fieldname.Value)`など) です。  
  
 *スコープ (scope)*  
 (**文字列**) 省略可。 **expression** で指定された直前の値を取得する対象となるスコープを示すグループやデータ領域の名前、または NULL ( [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]では *Nothing*) です。  
  
## <a name="return-type"></a>戻り値の型  
 **Variant** または **Binary**を返します。  
  
## <a name="remarks"></a>解説  
 **Previous** 関数は、すべての並べ替えおよびフィルター処理が適用された後、指定されたスコープで評価された式の直前の値を返します。  
  
 *expression* に集計が含まれていない場合、 **Previous** 関数では、レポート アイテムの現在のスコープが既定になります。  
  
 詳細グループで、直前の詳細行のフィールド参照の値を指定するには **Previous** を使用します。  
  
> [!NOTE]  
>  **Previous** 関数では、詳細グループでのみフィールド参照がサポートされます。 たとえば、詳細グループのテキスト ボックスの場合、 `=Previous(Fields!Quantity.Value)` では、直前の行から `Quantity` フィールドのデータが返されます。 この式が先頭行にある場合は、NULL (**では** Nothing [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]) が返されます。  
  
 既定のスコープを使用する集計関数が *expression* に含まれている場合、 **Previous** では、集計関数の呼び出しで指定されたスコープの直前のインスタンス内のデータを集計します。  
  
 既定以外のスコープを指定する集計関数が *expression* に含まれている場合、 *Previous* 関数の **scope** パラメーターには、集計関数の呼び出しで指定されたスコープのコンテナー スコープを指定する必要があります。  
  
 関数 **Level**、 **InScope**、 **Aggregate** 、 **Previous** は、 *expression*パラメーターで使用できません。 集計関数に *recursive* パラメーターを指定することはサポートされていません。  
  
 詳細については、「[集計関数リファレンス (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>Description  
 次のコード例は、データ領域の既定のデータ行に配置されると、直前の行の `LineTotal` フィールドの値が表示されます。  
  
### <a name="code"></a>コード  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a>Description  
 次の例では、特定の月日の売上合計と、前年のその月日の値を計算する式を示します。 この式は、子グループ `GroupbyDay`に属する行内のセルに追加されます。 その親グループは `GroupbyMonth`で、このグループの親グループは `GroupbyYear`です。 この式では、GroupbyDay (既定のスコープ) の結果、次に `GroupbyYear` (親グループ `GroupbyMonth`の親) の結果が表示されます。  
  
 たとえば、親グループが `Year`、その子グループが `Month`、そのまた子グループが `Day` という名前のデータ領域 (入れ子レベル 3) の場合、 グループ `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` に関連付けられた行内の式 `Day` は、前年の同じ月日の売上高の値を返します。  
  
### <a name="code"></a>コード  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a>参照  
 [レポート &#40; 内の式の使用レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例と &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式 &#40; 内のデータ型レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [式のスコープの合計、集計、および組み込みコレクション & #40 です。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  