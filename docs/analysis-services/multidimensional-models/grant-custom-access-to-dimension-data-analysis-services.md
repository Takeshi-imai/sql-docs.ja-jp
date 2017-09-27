---
title: "付与 (Analysis Services) のディメンション データへのカスタム アクセス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.roledesignerdialog.dimensiondata.f1
helpviewer_keywords:
- dimensions [Analysis Services], security
- AllowedSet property
- IsAllowed property
- DeniedSet property
- user access rights [Analysis Services], dimensions
- custom dimension data access [Analysis Services]
- permissions [Analysis Services], dimensions
- DefaultMember property
- VisualTotals property
- ApplyDenied property
ms.assetid: b028720d-3785-4381-9572-157d13ec4291
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 4ef09ff12c41b6bb5a7610134cb317a81caaf3cf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="grant-custom-access-to-dimension-data-analysis-services"></a>ディメンション データへのカスタム アクセス権の付与 (Analysis Services)
  キューブに対する読み取りアクセスを有効にすると、ディメンション メンバー (キューブで使用されるすべてのメジャーを含むメジャー ディメンションのメジャーを含む) へのアクセスを明示的に許可または拒否する追加の権限を設定できます。 たとえば、再販業者のカテゴリが複数ある場合は、特定のビジネスの種類のデータを除外する権限を設定できます。 次の図は、Reseller ディメンションでウェアハウスのビジネスの種類へのアクセスを拒否した場合の、前後の影響を比較しています。  
  
 ![ピボット テーブルとディメンション メンバーなし](../../analysis-services/multidimensional-models/media/ssas-permsdimdenied.png "ピボット テーブルとディメンション メンバーなし")  
  
 既定では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] キューブからデータを読み込めるのであれば、そのキューブに関連付けられているすべてのメジャーおよびディメンション メンバーに対する読み込み権限は自動的に付与されています。 多くのシナリオではこの動作で十分ですが、同じディメンションのそれぞれのユーザーに応じたさまざまなレベルのアクセスと共に、よりセグメント化された承認戦略がセキュリティ要件で求められる場合があります。  
  
 アクセスを制限するには、アクセスを許可するメンバー (AllowedSet) または拒否するメンバー (DeniedSet) を選択します。 そのためには、ロールに含めるまたはロールから除外するディメンション メンバーを選択または選択解除します。  
  
 基本的なディメンション セキュリティが最も簡単です。ロールに含めるまたはロールから除外するディメンション属性と属性階層を選択するだけです。 強化されたセキュリティはより複雑なため、MDX スクリプトの専門知識が必要です。 両方の方法について次に説明します。  

> [!NOTE]  
>  次の手順では、MDX でクエリを発行するクライアント接続を想定しています。 クライアントが Power BI の Power View などの DAX を使用する場合、ディメンションのセキュリティはクエリ結果で明らかになりません。 詳細については、「[多次元モデルの Power View について](/sql-docs/docs/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models)」を参照してください。
      
## <a name="prerequisites"></a>前提条件  
 すべてのメジャーまたはディメンション メンバーがカスタム アクセス シナリオで使用できる訳ではありません。 ロールが既定のメジャーまたはメンバーへのアクセスを制限したり、メジャー式の一部であるメジャーへのアクセスを制限したりすると、接続は失敗します。  
  
 **ディメンション セキュリティに対する障害 (既定のメジャー、既定のメンバー、メジャー式に使用されるメジャー) を確認します。**  
  
1.  SQL Server Management Studio でキューブを右クリックし、 **[キューブをスクリプト化]** | **[ALTER]** | **[新しいクエリ エディター ウィンドウ]**の順にクリックします。  
  
2.  **DefaultMeasure**を探します。 キューブに対して 1 つと、パースペクティブごとに 1 つ見つかります。 ディメンション セキュリティを定義する際、既定のメジャーへのアクセスを制限しないようにしてください。  
  
3.  次に、 **MeasureExpression**を探します。 メジャー式は、計算に基づいたメジャーです。通常、この計算には他のメジャーが含まれます。 制限するメジャーが、式では使用されていないことを確認してください。 あるいは、アクセスを制限し、同時にそのメジャーに対するすべての参照をキューブ全体から必ず除外します。  
  
4.  最後に、 **DefaultMember**を探します。 属性の既定のメンバーとして機能する属性をメモしておきます。 ディメンション セキュリティを設定する場合は、これらの属性に制限を設けないようにしてください。  
  
## <a name="basic-dimension-security"></a>基本的なディメンション セキュリティ  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、オブジェクト エクスプローラーで適切なデータベースの **[ロール]** を展開し、データベース ロールをクリックするか、新しいデータベース ロールを作成します。  
  
     ロールは、既にキューブへの読み込みアクセス権を持っている必要があります。 詳細については、「 [Grant cube or model permissions &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md) を参照してください。  
  
2.  **[ディメンション データ]** | **[基本]**で、権限を設定するディメンションを選択します。  
  
3.  属性階層を選択します。 属性の一部は、利用できない場合があります。 **[AttributeHierarchyEnabled]** を持つ属性のみが、 **[属性階層]** の一覧に表示されます。  
  
4.  アクセスを許可または拒否するメンバーを選択します。 既定では、 **[すべてのメンバーを選択する]** オプションでアクセスを許可します。 この既定を維持し、 **[メンバーシップ]** ペイン内の Windows ユーザー アカウントとグループ アカウントに対して表示しない個々のメンバーを、このロールによってオフにすることをお勧めします。 この利点は、このロールを介して接続するユーザーが、その後の処理操作で追加される新しいメンバーを自動的に使用できるようになることです。  
  
     また、 **[すべてのメンバーの選択を解除する]** を実行してすべてのアクセスを取り消してから、許可するメンバーを選択することもできます。 その後の処理操作で、新しいメンバーは、アクセスを許可するようにディメンション データ セキュリティが手動で編集されるまで表示されません。  
  
5.  必要に応じて **[詳細設定]** をクリックし、この属性階層の **[表示部分の合計]** を表示します。 このオプションは、ロールを介して使用できるメンバーに基づいて集計を再計算します。  
  
    > [!NOTE]  
    >  ディメンション メンバーを取り除く権限を適用する場合は、集計合計は自動的には再計算されません。 権限が適用される前に、属性階層の **All** メンバーが、値 200 を返すとします。 一部のメンバーへのアクセスを拒否する権限の適用後、 **All** は、ユーザーに対して表示されているメンバー値がはるかに少ない場合でも、200 を返します。 キューブのコンシューマーが混乱するのを避けるために、 **All** メンバーを属性階層のすべてのメンバーの集計値ではなく、ロール メンバーがアクセスできるメンバーの集計値となるように構成できます。 この動作を呼び出すには、ディメンション セキュリティの構成中に **[詳細設定]** タブで、 **[表示部分の合計]** を有効にします。 有効になると、集計値は事前計算された集計値から取得されるのではなく、クエリの実行時に計算されます。 これにより、クエリのパフォーマンスに大きな影響が出る可能性があるため、必要な場合にのみ使用してください。  
  
## <a name="hiding-measures"></a>メジャーの非表示  
 「 [セル データへのカスタム アクセス権の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)」で、セル データだけでなく、メジャーのすべての表示部分を完全に非表示にするには、ディメンション メンバーに対する権限が必要であることが説明されています。 ここでは、メジャーのオブジェクト メタデータへのアクセスを拒否する方法について説明します。  
  
1.  **ディメンション データ** | **基本**、表示されるまで、キューブ ディメンションを選択し、ディメンションの一覧を下にスクロール**Measures ディメンション**です。  
  
2.  メジャーの一覧から、このロールを使用して接続しているユーザーに対しては表示しないメジャーのチェック ボックスをオフにします。  
  
> [!NOTE]  
>  ロール セキュリティを解除できるメジャーを識別する方法については、前提条件を確認してください。  
  
## <a name="advanced-dimension-security"></a>強化されたディメンション セキュリティ  
 MDX の専門知識がある場合は、別の方法として、アクセスが許可または拒否されたメンバー用の条件を設定するための MDX 式を記述します。 **[ロールの作成]** | **[ディメンション データ]** | **[詳細設定]** の順にクリックして、スクリプトを指定します。  
  
 MDX ビルダーを使用すると、MDX ステートメントを記述できます。 詳細については、「[MDX ビルダー &#40;Analysis Services - 多次元データ&#41;](http://msdn.microsoft.com/library/fecbf093-65ea-4e1b-b637-f04876f1cb0f)」を参照してください。 **[詳細設定]** タブには次のオプションがあります。  
  
 **属性**  
 メンバーのセキュリティを管理する属性を選択します。  
  
 **[許可されたメンバー セット]**  
 AllowedSet は、空のメンバー (既定)、すべてのメンバー、または一部のメンバーに解決されます。 属性へのアクセスを許可しているにもかかわらず、許可されたセットにメンバーを定義していない場合は、すべてのメンバーへのアクセスが許可されます。 属性へのアクセスを許可していて、属性メンバーの特定のセットを定義した場合は、明示的に許可されているメンバーのみが表示されます。  
  
 AllowedSet を作成すると、属性が複数階層に参加する際に波及効果があります。 たとえば、ロールが Washington 州へのアクセスを許可するとします (ロールから、Washington 州 にある会社の営業部門に権限が付与されるというシナリオを想定します)。 このロールを使用して接続しているユーザーの場合、先祖 (United States) または子孫 (Seattle および Redmond) を含むクエリに対しては、Washington 州を含むチェーンにあるメンバーのみが表示されます。 他の州は明示的に許可されていないため、与える影響は拒否された場合と同じです。  
  
> [!NOTE]  
>  空の属性メンバー セット ({}) を定義した場合、属性メンバーはデータベース ロールにはまったく表示されません。 許可されたセットが存在しない場合は、空のセットが存在するものとして解釈されます。  
  
 **[拒否されたメンバー セット]**  
 DeniedSet プロパティは、空のメンバー、すべてのメンバー (既定)、または一部の属性メンバーに解決されます。 拒否されたセットに特定の属性メンバーのセットのみが含まれている場合、データベース ロールに対しては、それらの特定のメンバーと子孫 (属性が複数階層にある場合) へのアクセスのみが拒否されます。 Washington 州の営業部門の例を考えてみましょう。 Washington が DeniedSet に配置されている場合、このロールを使用して接続しているユーザーには、Washington 以外のすべての州とそれらの子孫の属性が表示されます。  
  
 前のセクションで説明したように、拒否されたセットは固定コレクションです。 その後、アクセスが拒否される必要のある新しいメンバーが処理によって追加された場合、このロールを編集して、それらのメンバーを一覧に追加する必要があります。  
  
 **[既定のメンバー]**  
 DefaultMember プロパティは、属性がクエリに明示的に含まれていない場合に、クライアントに返されるデータセットを決定します。 属性が明示的に含まれていない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では属性に対して次の既定メンバーのいずれかを使用します。  
  
-   データベース ロールで属性の既定メンバーを定義している場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではこの既定メンバーを使用します。  
  
-   データベース ロールが属性の既定メンバーを定義していない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では属性自体に定義されている既定メンバーを使用します。 属性の既定メンバーは、特別に指定していない限り、 **All** のメンバーになります (属性が非集計として定義されている場合を除く)。  
  
 たとえば、データベース ロールで、 **Male** を **Gender** 属性の既定のメンバーとして指定しているとします。 クエリに、 **Gender** 属性が明示的に含まれており、この属性に別のメンバーが指定されているのでない限り、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では男性顧客のみを含むデータセットを返します。 既定メンバーの設定の詳細については、「 [既定メンバーの定義](../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)」を参照してください。  
  
 **[表示部分の合計を表示する]**  
 VisualTotals プロパティは、表示される集計セル値がすべてのセル値に基づいて計算されるか、データベース ロールが表示可能なセル値のみに基づいて計算されるかを示します。  
  
 既定では、VisualTotals プロパティは無効になっています ( **False**に設定されています)。 この既定の設定では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、計算に使用するセル値の選択に時間を費やすことなく、すべてのセル値の合計をすばやく計算できるので、最大限のパフォーマンスが実現します。  
  
 ただし、VisualTotals プロパティを無効にすると、集計されたセル値を使用して、ユーザーのデータベース ロールにアクセス権のない属性メンバーの値をユーザーが推定しようとした場合に、セキュリティの問題が発生するおそれがあります。 たとえば、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では 3 つの属性メンバーの値を使用して、集計セル値を計算します。 データベース ロールには、これらの 3 つの属性メンバーのうちの 2 つを表示するためのアクセス権が許可されています。 集計セル値を使用すると、このデータベース ロールのメンバーは、3 番目の属性メンバーの値を推定できるようになります。  
  
 VisualTotals プロパティを **True** に設定すると、この危険を回避できます。 VisualTotals プロパティを有効にすると、データベース ロールでは、権限のあるディメンション メンバーの集計合計のみを表示できるようになります。  
  
 **[確認]**  
 このページに定義された MDX 構文をテストします。  
  
## <a name="see-also"></a>参照  
 [キューブ権限またはモデル権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)   
 [セルのデータ &#40; へのカスタム アクセスを許可します。Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)   
 [データ マイニング構造およびモデル &#40; に対する権限を付与します。Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)   
 [データ ソース オブジェクトに対する権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-data-source-object-analysis-services.md)  
  
  