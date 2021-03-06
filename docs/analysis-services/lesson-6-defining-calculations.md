---
title: "レッスン 6: 計算の定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: e0a1e354-e879-4eb8-bb2b-6c3809e32cb6
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 9491f840fdf7d1848fd4cc6bdf23bf98a4acd4b3
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="lesson-6-defining-calculations"></a>レッスン 6 : 計算の定義
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

このレッスンでは、多次元式 (MDX) の式またはスクリプトである計算を定義する方法について学習します。 計算を使用すると、計算されるメンバーや名前付きセットを定義できます。また、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] キューブの機能を拡張するさまざまなスクリプト コマンドを実行できます。 たとえば、サブキューブを定義し、計算をサブキューブ内のセルに割り当てるスクリプト コマンドを実行できます。  
  
新しい計算をキューブ デザイナーで定義すると、その計算はキューブ デザイナーの **[計算]** タブの **[スクリプト オーガナイザー]** ペインに追加され、特定の計算の種類に対応するフィールドが **計算式** ペインの計算フォームに表示されます。 複数の計算は、 **[スクリプト オーガナイザー]** ペイン内に表示されている順番で実行されます。 計算の順序を変えるには、特定の計算を右クリックして **[上へ移動]** または **[下へ移動]**をクリックします。または、特定の計算をクリックし、 **[計算]** タブのツール バーにある **[上へ移動]** または **[下へ移動]** アイコンをクリックします。  
  
**[計算]** タブでは、 **計算式** ペイン内の次のビューを使用して、新しい計算の追加や、既存の計算の表示または編集を行えます。  
  
-   フォーム ビュー。 このビューには、1 つのコマンドの式とプロパティがグラフィック形式で表示されます。 MDX スクリプトを編集する場合は、式ボックスがフォーム ビューに表示されます。  
  
-   スクリプト ビュー。 このビューでは、すべての計算スクリプトがコード エディター内に表示されます。これを使用して、計算スクリプトを簡単に変更できます。 **計算式** ペインがスクリプト ビューになっているとき、 **[スクリプト オーガナイザー]** は非表示になります。 スクリプト ビューには、色分け表示、かっこの対応、オートコンプリート、MDX コード領域などの機能が用意されています。 MDX コード領域は展開や折りたたみが可能なので、容易に編集を行うことができます。  
  
**計算式** ペイン内でこれらのビューを切り替えるには、 **[計算]** タブのツール バーの **[フォーム ビュー]** または **[スクリプト ビュー]** をクリックします。  
  
> [!NOTE]  
> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がいずれかの計算の構文エラーを検出した場合、スクリプト ビュー内でエラーを修正するまでは、フォーム ビューが表示されません。  
  
また、ビジネス インテリジェンス ウィザードを使用して特定の計算をキューブに追加することもできます。 たとえば、このウィザードを使ってタイム インテリジェンスをキューブに追加できます。タイム インテリジェンスでは、期間対日付、移動平均、前期比成長率など、時間に関連した計算されるメンバーを定義します。 詳細については、「 [ビジネス インテリジェンス ウィザードを使用したタイム インテリジェンス計算の定義](../analysis-services/multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)」を参照してください。  
  
> [!IMPORTANT]  
> **[計算]** タブでは、計算スクリプトは CALCULATE コマンドで始まります。 CALCULATE コマンドはキューブ内のセルの集計を制御します。キューブ セルの集計方法を手動で指定する場合のみ、このコマンドを編集してください。  
  
詳細については、「 [計算](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)」および「 [多次元モデルの計算](../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)」を参照してください。  
  
> [!NOTE]  
> このチュートリアルの各レッスンの操作内容が反映されたプロジェクトを、オンラインで入手できます。 途中のレッスンから開始する場合は、前のレッスンの操作内容が反映されたプロジェクトを作業の開始点として使用できます。 このチュートリアルのサンプル プロジェクトをダウンロードするには、[ここ](http://go.microsoft.com/fwlink/?LinkID=221866) をクリックしてください。  
  
このレッスンの内容は次のとおりです。  
  
[計算されるメンバーを定義します。](../analysis-services/lesson-6-1-defining-calculated-members.md)  
ここでは、計算されるメンバーを定義する方法について学習します。  
  
[名前付きセットを定義します。](../analysis-services/lesson-6-2-defining-named-sets.md)  
この作業では、名前付きセットを定義する方法について学習します。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 7: 主要業績評価指標を定義する &#40;です。Kpi&#41;](../analysis-services/lesson-7-defining-key-performance-indicators-kpis.md)  
  
## <a name="see-also"></a>参照  
[Analysis Services のチュートリアル シナリオ](../analysis-services/analysis-services-tutorial-scenario.md)  
[多次元モデリング &#40;です。Adventure Works チュートリアル &#41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
[名前付きセットを作成します。](../analysis-services/multidimensional-models/create-named-sets.md)  
[計算されるメンバーを作成します。](../analysis-services/multidimensional-models/create-calculated-members.md)  
  
  
  
