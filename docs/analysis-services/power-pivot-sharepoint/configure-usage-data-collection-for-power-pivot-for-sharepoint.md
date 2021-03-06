---
title: "使用状況データ収集の構成 (Power Pivot for SharePoint |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 955ca6d6-9d5b-47a4-a87c-59bd23f1bf74
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 60e8c6ab0537a8757d6a75b05e4788dc4a29768f
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="configure-usage-data-collection-for-power-pivot-for-sharepoint"></a>使用状況データ収集の構成 (対象は Power Pivot for SharePoint)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
使用状況データ収集は、ファーム レベルの SharePoint 機能です。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint では、このシステムを使用および拡張して、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のデータやサービスがどのように使用されているかを示すレポートが [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードに用意されています。 SharePoint のインストール方法によっては、使用状況データ収集がファームに対して無効になっていることがあります。 ファーム管理者は、使用状況のログ記録を有効にして、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードに表示される使用状況データを作成する必要があります。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードの使用状況データの詳細については、「 [PowerPivot 管理ダッシュボードと使用状況データ](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)」を参照してください。  
  
 **このトピックの内容**  
  
 [使用状況データ収集の有効化とデータ収集を開始するイベントの選択](#events)  
  
 [ログ ファイルの場所の設定](#configdb)  
  
 [使用状況データ収集に使用されるタイマー ジョブの構成](#jobs)  
  
 [使用状況データ履歴の格納期間の制限](#confighist)  
  
 [レポート用の高速、中速、および低速のクエリ応答カテゴリの定義](#qrh)  
  
 [クエリ統計を使用状況データ収集システムに報告する頻度の指定](#ttr)  
  
 [Power Pivot サービス アプリケーションのページを開いて構成設定にアクセスする](#openconfig)  
  
 [Power Pivot 使用状況データ収集の既定の構成](#defaultconfig)  
  
> [!IMPORTANT]  
>  使用状況データは、ユーザーがデータとリソースにどのようにアクセスしているかを理解するための手がかりを提供しますが、サーバー操作とユーザー アクセスについての信頼性の高い永続的なデータを保証するわけではありません。 たとえば、サーバーが再起動した場合、イベント使用状況データは失われ、復元できなくなります。 同様に、一時ログ ファイルが最大サイズに達した場合、ファイルを消去するまで、新しいデータは追加されません。 監査機能が必要な場合は、SharePoint が提供するワークフローおよびコンテンツの種類に関する機能を使用して、ファーム用の監査サブシステムを構築することを検討してください。 詳細については、製品およびコミュニティのマニュアルを Web 上で検索してください。  
  
##  <a name="events"></a> 使用状況データ収集の有効化とデータ収集を開始するイベントの選択  
 SharePoint サーバーの全体管理で使用状況データ収集を構成します。  
  
1.  サーバーの全体管理で **[監視]**をクリックします。  
  
2.  **[レポート]**セクションで、 **[使用状況と正常性のデータ収集の構成]**をクリックします。  
  
3.  **[利用状況データの収集を有効にする]**をオンにします。  
  
4.  **[ログ対象イベント]** セクションで、チェック ボックスをオンまたはオフにして、次の Analysis Services イベントを有効または無効にします。  
  
    |イベント|Description|  
    |-----------|-----------------|  
    |**[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 接続**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 接続イベントは、ユーザーに代わって実行される [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバー接続を監視するために使用します。|  
    |**[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 読み込みデータの使用状況**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 読み込みデータ使用状況は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データをサーバーのメモリに読み込む要求を監視するために使用します。 読み込みイベントは、コンテンツ データベースまたはキャッシュから読み込まれた [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソースに対して生成されます。|  
    |**[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] アンロード データの使用状況**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] アンロード データ使用状況は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソースを非アクティブ期間の後にアンロードする要求を監視するために使用します。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソースのディスクへのキャッシュは、アンロード イベントとして報告されます。|  
    |**[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クエリの使用状況**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クエリの使用状況は、 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] インスタンスに読み込まれるデータのクエリ処理時間を監視するために使用します。|  
  
    > [!NOTE]  
    >  サーバー状態操作とデータ更新操作でも使用状況データが生成されますが、これらの処理に関連するイベントはありません。  
  
5.  ログ ファイルの場所を更新することもできます。 詳細については、次のセクションを参照してください。  
  
6.  **[OK]** をクリックして変更を保存します。  
  
7.  必要に応じて、すべてのメッセージをログに記録するか、エラーのみをログに記録するかを指定できます。 イベント メッセージのスロットル方法の詳細については、「[SharePoint ログ ファイルと診断ログの構成と表示 &#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md)」を参照してください。  
  
##  <a name="configdb"></a> ログ ファイルの場所の設定  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 使用状況データは、まずローカル サーバー上の使用状況ログ ファイルに格納され、その後 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション データベースに定期的に移動されます。 ログ ファイルの場所は、サーバーの全体管理で設定します。 既定の場所は次のとおりです。  
  
 `C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\logs`  
  
 これらのプロパティを表示または変更するには、 **[Usage and Health data collection]** ページを使用します。  
  
1.  サーバーの全体管理の [ホーム] ページで、 **[監視]**をクリックします。  
  
2.  [監視] セクションで、 **[使用状況と正常性のデータ収集の構成]**をクリックします。  
  
3.  [使用状況データ収集の設定] で、ファイルの場所、名前、最大ファイル サイズを表示または変更します。 指定したファイル サイズが小さすぎる場合、ファイル サイズが最大限に達すると、コンテンツを中央の使用状況データ収集データベースに移動するまで、新しいエントリは追加されなくなります。  
  
##  <a name="jobs"></a> 使用状況データ収集に使用されるタイマー ジョブの構成  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーの状態と使用状況データは、次に示す 2 つのタイマー ジョブにより、使用状況データ収集システムの別々の場所に移動されます。  
  
-   "Microsoft SharePoint Foundation 利用状況データのインポート" タイマー ジョブは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 使用状況データを [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション データベースに移動します。  
  
-   "[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボード処理タイマー ジョブ" は、組み込み管理レポートのデータ ソースである [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックにデータを移動します。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードに表示される管理レポートをより頻繁に更新する必要がある場合は、次の手順を実行します。  
  
1.  サーバーの全体管理で **[監視]**をクリックします。  
  
2.  クリックして **[ジョブ定義の確認]** をクリックします。 **[タイマー ジョブ]** セクションを確認します。  
  
3.  **[Microsoft SharePoint Foundation 利用状況データのインポート]**をクリックします。  
  
4.  **[今すぐ実行]**をクリックします。 **[今すぐ実行]** ボタンが無効になっている場合は、 **[有効]** をクリックしてから **[今すぐ実行]**をクリックします。  
  
5.  [ジョブの定義] リストで、 **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボード処理タイマー ジョブ**をクリックします。  
  
6.  **[今すぐ実行]**をクリックします。  
  
7.  レポートをチェックして、更新データを確認します。 詳細については、「 [Power Pivot Management Dashboard and Usage Data](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)」を参照してください。  
  
##  <a name="confighist"></a> 使用状況データ履歴の格納期間の制限  
 イベント (接続、読み込み、アンロード、およびオンデマンド クエリ処理) およびデータ更新 (スケジュールされたデータ処理) に対して、使用状況データ履歴が格納されます。 使用状況データは SharePoint 使用状況データ収集システムを通じて収集されますが、レポート データは長期的な保存のために [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] アプリケーション データベースとレポート データベースに移動されます。 使用状況データ履歴の設定によって、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] アプリケーション データベースで使用状況データを維持する期間が制御されます。 同じ [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション データベースに格納されたすべての種類の使用状況データに、同じ制限が同様に適用されます。  
  
1.  [Power Pivot サービス アプリケーションのページを開きます](#openconfig)。  
  
2.  **[使用状況データ コレクション]** セクションの **[使用状況データの履歴]**で、各ブックのデータ更新操作の記録を保持する日数を入力します。  
  
    -   既定値は 365 日です。  
  
    -   0 の場合、使用状況データが無限に保持される無制限のストレージが指定されます。  
  
    -   または、1 ～ 5,000 の範囲を指定できます。  
  
     保持期間の日数を減らすと、新しい制限を超えるすべてのデータが削除されます。 たとえば、値を 365 から 30 に変更すると、31 日以上前に発生したすべての履歴情報の使用状況データが削除されます。 最近の 30 日間のデータのみが保持されます。  
  
     データは、次のイベントが発生したときに実際に削除されます。 使用状況データ履歴の制限は、システムがイベントを処理したときにのみ確認されます。  
  
3.  **[OK]**をクリックします。  
  
 使用状況データが収集および格納されるしくみの詳細については、「 [Power Pivot 使用状況データ収集](../../analysis-services/power-pivot-sharepoint/power-pivot-usage-data-collection.md)」を参照してください。  
  
##  <a name="qrh"></a> レポート用の高速、中速、および低速のクエリ応答カテゴリの定義  
 クエリ応答のパフォーマンスは、定義済みのカテゴリに基づいて計測されます。このカテゴリでは、完了に要する時間に応じた要求と応答のサイクルが定義されています。 この定義済みのカテゴリの種類には、簡易応答、迅速な応答、想定される応答、長い応答、および超過応答があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーへのすべての要求は、完了に要する時間に基づいて、いずれかのカテゴリに分類されます。  
  
 クエリ応答情報は、利用状況レポートで使用されます。 レポート内では、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] システムのパフォーマンス傾向をより詳しく解明するために、各カテゴリを異なる方法で使用します。 たとえば、簡易要求は完全に除外されます。これは、簡易要求を除外することによってデータ内の不要な情報が削除され、残りのカテゴリを使用して意味のある傾向が示されるためです。 一方、長期要求または超過要求の統計は、管理者またはブック所有者が修正作業をすぐに実行できるように、レポートで強調されます。  
  
 カテゴリを追加または削除することも可能ですが、カテゴリとカテゴリの境界を決定する上限および下限を定義できます。 組織でサービス レベル契約 (SLA) を使用してサーバーの可用性およびパフォーマンスの許容可能なレベルを定義する場合、作成した SLA を反映するように、これらのカテゴリを調整できます。  
  
1.  [Power Pivot サービス アプリケーションのページを開きます](#openconfig)。  
  
2.  **[使用状況データ コレクション]** セクションの **[簡易応答の上限]** に、簡易応答を完了するための上限を設定する値 (ミリ秒単位) を入力します。 このカテゴリに分類される要求には、サーバー ping、セッション開始、メタデータ クエリなどがあります。 既定値は 500 ミリ秒 (0.5 秒) です。  
  
3.  [迅速な要求の上限] に、迅速な応答を完了するための上限を設定する値 (ミリ秒単位) を入力します。 このカテゴリに分類される要求には、きわめて小規模なデータセットに対するクエリや、大規模なデータセットのメタデータ サーバーに対するクエリがあります。 既定値は 1,000 ミリ秒 (1 秒) です。  
  
4.  **[想定される応答の上限]**に、想定または平均のタイム フレーム内で応答を完了するための上限を設定する値 (ミリ秒単位) を入力します。 このカテゴリに分類される要求には、データのビューアーへの読み込みがあります。 既定値は 3,000 ミリ秒 (3 秒) です。  
  
5.  **[長い応答の上限]**に、実行時間が長い応答を完了するための上限を設定する値 (ミリ秒単位) を入力します。 このカテゴリに分類される要求は、想定よりも長い時間実行されますが、許容範囲には収まります。 既定値は 10,000 ミリ秒 (10 秒) です。  
  
     この制限を超えるすべての要求は、 *超過*と分類されます。 *超過*についての構成可能なしきい値はありません。 [長い応答の上限] で指定した上限から推測されます。 超過カテゴリに分類される要求は、定義した SLA によって許容される時間よりも長く実行される要求です。  
  
6.  **[OK]**をクリックします。  
  
##  <a name="ttr"></a> クエリ統計を使用状況データ収集システムに報告する頻度の指定  
 レポート間隔によって、クエリ統計を使用状況データ収集システムに報告する頻度を指定します。 クエリ統計は、プロセス内で蓄積され、単一のイベントとして定期的に報告されます。 この間隔を調整して、ログ ファイルに書き込む頻度を増減させることができます。  
  
1.  [Power Pivot サービス アプリケーションのページを開きます](#openconfig)。  
  
2.  **[使用状況データ コレクション]** セクションの **[クエリをレポートする間隔]**に、サーバーがすべてのカテゴリ (簡易応答、迅速な応答、想定される応答、長い応答、および超過応答) のクエリ統計を、単一のイベントとして使用状況データ収集システムに報告するまでの秒数を入力します。  
  
    -   範囲は、1 から任意の正の整数までです。  
  
    -   既定値は 300 秒 (5 分) です。 この値は、さまざまなアプリケーションおよびサービスを実行する動的ファーム環境に推奨されます。  
  
     この値を大幅に増やすと、統計データが報告前に失われる可能性があります。 たとえば、サービスを再起動すると、クエリ統計が失われます。 逆に、組み込みの利用状況レポートに十分なデータが表示されない場合、間隔を短くして、レポート間隔イベントをより頻繁に取得することを検討してください。  
  
3.  **[OK]**をクリックします。  
  
##  <a name="openconfig"></a> Power Pivot サービス アプリケーションのページを開いて構成設定にアクセスする  
 サービス アプリケーションの設定を変更するには、ファームまたはサービスの管理者であることが必要です。 ファームで複数の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを定義した場合は、それぞれを個別に変更する必要があります。  
  
1.  SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]**の **[サービス アプリケーションの管理]**をクリックします。  
  
2.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを検索します。 サービス アプリケーションは、型で識別できます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションの型が、 **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション**ではありません。  
  
3.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション名をクリックします。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードが開きます。  
  
4.  **[アクション]**で **[サービス アプリケーションの設定の構成]**をクリックします。 [ [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションの設定] ページが開きます。  
  
##  <a name="defaultconfig"></a> Power Pivot 使用状況データ収集の既定の構成  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス操作の使用状況データ収集を既定の設定で有効にすると、Analysis Services の統合機能をサポートするアプリケーションで、使用状況データ収集をすぐに使用することができます。 既定の設定には、使用状況データ収集を開始するイベント、使用状況データを格納する期間の制限、およびクエリ応答時間を分類するためのしきい値が含まれます。  
  
 次の表に、使用状況データ収集の構成の既定値を示します。  
  
|設定|既定値|型|有効な範囲|  
|-------------|-------------------|----------|-----------------|  
|**Analysis Services 使用状況イベント** (接続、読み込み、アンロード、要求)|\<enabled>|ブール値|これらの値は、有効または無効のいずれかです。|  
|**Query Reporting interval**|300 (秒)|Integer|1 から任意の正の整数まで。 既定値は 5 分です。|  
|**Usage data history**|365 (日)|Integer|0 は無制限を示しますが、履歴データが期限切れとなる上限を設定し、履歴データを自動的に削除することもできます。 限られた保持期間の有効な値は 1 ～ 5,000 (日) です。|  
|[簡易応答の上限]|500 (ミリ秒単位)|Integer|簡易要求と応答のやり取りが完了するまでの時間を定義する上限を設定します。 0 ～ 500 ミリ秒で完了する要求は簡易要求であり、レポートでは無視されます。|  
|迅速な応答の上限|1000 (ミリ秒単位)|Integer|迅速な要求と応答のやり取りが完了するまでの時間を定義する上限を設定します。|  
|想定される応答の上限|3000 (ミリ秒単位)|Integer|想定される要求と応答のやり取りが完了するまでの時間を定義する上限を設定します。|  
|長い応答の上限|10,000 (ミリ秒)|Integer|長い要求と応答のやり取りが完了するまでの時間を定義する上限を設定します。 この上限を超えるすべての要求は、上限のしきい値がない超過カテゴリに分類されます。|  
  
## <a name="see-also"></a>参照  
 [構成設定のリファレンス &#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Power Pivot 使用状況データ収集](../../analysis-services/power-pivot-sharepoint/power-pivot-usage-data-collection.md)  
  
  
