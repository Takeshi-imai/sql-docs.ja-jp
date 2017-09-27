---
title: "レポート履歴 (SharePoint 統合モードで Reporting Services) の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- report history [Reporting Services], SharePoint
ms.assetid: e57ec746-05ae-4ff6-8e39-6cde87310daa
caps.latest.revision: 12
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3e1388fba5963d5571d293f2d995c73bb3d83d3b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="create-report-history-reporting-services-in-sharepoint-integrated-mode"></a>レポート履歴の作成 (Reporting Services の SharePoint 統合モード)
  レポート履歴とは、時間の経過と共に作成されるレポート スナップショットの集まりです。 各スナップショットは、レポート作成時の状態でのレポートのコピーであり、 スナップショット作成時点のレポートのレイアウトとデータが含まれています。 レンダリング情報はスナップショットに保存されません。 レポート履歴のスナップショットを開くと、スナップショットはレポート ビューアー Web パーツに HTML 形式で表示されます。 表示されたスナップショットは、別のアプリケーション形式にエクスポートできます。  
  
 レポート履歴を作成するには、レポートの自動実行が可能な状態である必要があります (つまり、レポート サーバー側で、ユーザーの操作を必要とせずにレポートを実行できる必要があります)。 レポートを含むライブラリに対する、"アイテムの編集" 権限が必要です。 レポート履歴を表示または削除するには、"バージョンの表示" 権限または "バージョンの削除" 権限が必要です。  
  
### <a name="to-create-a-snapshot-or-report-history-on-demand"></a>スナップショットまたはレポート履歴を必要に応じて作成するには  
  
1.  レポートをポイントします。  
  
2.  クリックして下矢印を表示し、 **[レポート履歴の表示]**をクリックします。  
  
3.  **[新しいスナップショット]**をクリックします。 レポート履歴にスナップショットを作成する権限がない場合、このボタンは表示されません。  
  
4.  作成したスナップショットを表示するには、一覧から作成したスナップショットを選択します。 各スナップショットは、スナップショットの作成日時を示すタイムスタンプで識別できます。 スナップショットは、名前を変更したり、別の場所に移動したり、内容を変更したりすることはできません。  
  
### <a name="to-schedule-report-history"></a>レポート履歴をスケジュールするには  
  
1.  レポートをポイントします。  
  
2.  クリックして下矢印を表示し、 **[処理オプションの管理]**を選択します。  
  
3.  **[履歴スナップショットのオプション]**の **[スケジュールに従ってレポート履歴スナップショットを作成する]**をクリックします。  
  
4.  使用するスケジュール情報が含まれている共有スケジュールがある場合は、 **[次の共有スケジュールで実行する]** をクリックし、使用するスケジュールを選択します。 それ以外の場合は、 **[カスタム スケジュールで実行する]**をクリックし、 **[構成]** をクリックして、定期的にレポート履歴を作成するためのオプションを指定します。  
  
### <a name="to-create-report-history-when-data-is-refreshed-in-a-report"></a>レポートのデータが更新されたときにレポート履歴を作成するには  
  
1.  レポートをポイントします。  
  
2.  クリックして下矢印を表示し、 **[処理オプションの管理]**を選択します。  
  
3.  **[履歴スナップショットのオプション]**の **[すべてのレポート データ スナップショットをレポート履歴に保存します]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [処理オプション &#40; を設定します。Reporting Services の SharePoint モード &#41; と統合](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
  