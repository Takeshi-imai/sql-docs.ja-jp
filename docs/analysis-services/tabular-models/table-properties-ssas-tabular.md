---
title: "テーブルのプロパティ |Microsoft ドキュメント"
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.custom: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.tableprop.f1
ms.assetid: 16d3347b-7e43-4a6b-9956-fdd6ede092e6
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 202902448a31fda27ab2c4d8c0bc894cc50da3db
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="table-properties"></a>Table Properties 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
この記事では、表形式モデル テーブルのプロパティについて説明します。 ここで説明するプロパティは、ソースのどの列をインポートするかを定義する [テーブルのプロパティの編集] ダイアログ ボックスのプロパティとは異なります。  
  
 このトピックのセクション:  
  
-   [テーブルのプロパティ](#bkmk_properties)  
  
-   [テーブル プロパティの設定を構成する](#bkmk_config_prop)  
  
##  <a name="bkmk_properties"></a> テーブルのプロパティ  
 **基本**  
  
|プロパティ|既定の設定|Description|  
|--------------|---------------------|-----------------|  
|**接続名**|\<接続名 >|テーブルのデータ ソースに対する接続の名前。<br /><br /> 接続を編集するには、ボタンをクリックします。|  
|**[非表示]**|False|レポート クライアント フィールドの一覧で、テーブルを非表示にするかどうかを指定します。|  
|**パーティション**||テーブルのパーティションは、 **[プロパティ]** ウィンドウに表示できません。 パーティションを表示、作成、または編集するには、ボタンをクリックしてパーティション マネージャーを開きます。|  
|**ソース データ**||テーブルのソース データは、 **[プロパティ]** ウィンドウに表示できません。 ソース データを表示または編集するには、ボタンをクリックして [テーブルのプロパティの編集] ダイアログ ボックスを開きます。|  
|**テーブルの説明**||テーブルの説明文です。<br /><br /> [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]では、フィールド一覧のこのテーブルにエンド ユーザーがカーソルを重ねると、ツールヒントとしてこの説明が表示されます。|  
|**テーブル名**|\<フレンドリ名 >|テーブルの表示名を指定します。 テーブルのインポート ウィザードを使用してテーブルをインポートするとき、またはインポート後の任意の時点で、テーブル名を指定できます。 モデル内のテーブル名は、ソースに関連付けられているテーブルとは異なる場合があります。 テーブル表示名は、レポート クライアント アプリケーション フィールドのリストおよび [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のモデル データベース内に表示されます。|  
  
 **レポートのプロパティ**  
  
 詳細な説明とレポートのプロパティの構成については、次を参照してください。 [Power View レポート プロパティ](../../analysis-services/tabular-models/power-view-reporting-properties-ssas-tabular.md)です。  
  
|プロパティ|既定の設定|Description|  
|--------------|---------------------|-----------------|  
|**既定のフィールド セット**|||  
|テーブルの動作|||  
  
##  <a name="bkmk_config_prop"></a> テーブル プロパティの設定を構成する  
  
1.  モデル デザイナーのデータ ビューでテーブル (タブ) をクリックするか、ダイアグラム ビューでテーブルのヘッダーをクリックします。  
  
2.  **[プロパティ]** ウィンドウで、プロパティをクリックして値を入力するか、ボタンをクリックして追加の構成オプションを選択します。  
  
  
