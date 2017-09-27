---
title: "カスタム コンポーネントに複数バージョン対応サポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server (starting with 2016)
ms.assetid: ec611374-16bf-4a56-8fd9-45d3ddd7befc
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 57ac95d7883ce47e1a39d4d50d3f60b968bccf21
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="support-multi-targeting-in-your-custom-components"></a>カスタム コンポーネントに複数バージョン対応サポートします。
 使えるようになりました SSIS デザイナーで SQL Server Data Tools (SSDT) を作成、保守、およびそのターゲット SQL Server 2016、SQL Server 2014 または SQL Server 2012 のパッケージを実行します。 SSDT for Visual Studio 2015 を参照してください[最新の SQL Server の Data Tools をダウンロード](/sql-docs/docs/ssdt/download-sql-server-data-tools-ssdt)です。 

 ソリューション エクスプローラーで Integration Services プロジェクトを右クリックし、 **[プロパティ]** を選択すると、そのプロジェクトのプロパティ ページが開きます。 **[構成プロパティ]** の **[全般]**タブで、 **[TargetServerVersion]** プロパティを選択した後、[SQL Server 2016]、[SQL Server 2014]、または [SQL Server 2012] を選択します。  
   
 ![プロジェクトのプロパティ ダイアログ ボックスの TargetServerVersion プロパティ](../../integration-services/media/targetserverversion2.png "プロジェクトのプロパティ ダイアログ ボックスの TargetServerVersion プロパティ")  
 
 ## <a name="multiple-version-support-and-multi-targeting-for-custom-components"></a>複数のバージョンのサポートおよびカスタム コンポーネントのマルチ ターゲット
 
SSIS カスタム拡張機能の 5 種類のすべてでは、マルチ ターゲットをサポートします。
-   接続マネージャー
-   処理手順
-   列挙子
-   ログ プロバイダー
-   データ フロー コンポーネント

マネージ拡張機能の場合は、SSIS デザイナーには、指定された対象のバージョンについては、拡張機能のバージョンが読み込まれます。 例:
-   ターゲット バージョンが SQL Server 2012 の場合は、デザイナーは、2012年バージョンの拡張機能を読み込みます。
-   ターゲット バージョンが SQL Server 2016 の場合は、デザイナーは、拡張機能の 2016年バージョンを読み込みます。

COM 拡張機能は、マルチ ターゲットをサポートしていません。 SSIS デザイナーは、常に、現在のバージョンの SQL Server では、指定されたターゲット バージョンに関係なく、COM の拡張機能を読み込みます。

## <a name="add-basic-support-for-multiple-versions-and-multi-targeting"></a>複数のバージョンおよびマルチ ターゲットの基本的なサポートを追加します。

基本的なガイダンスについては、次を参照してください。 [SQL Server 2016 用 SSDT 2015 の複数バージョンのサポートによってサポートされる SSIS カスタム拡張を取得する](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/)です。 このブログの投稿では、次の手順や要件について説明します。

-   適切なフォルダーにアセンブリを展開します。

-   SQL Server 2014 と高いバージョンの拡張マップ ファイルを作成します。

## <a name="add-code-to-switch-versions"></a>バージョンを切り替えるコードを追加します。

### <a name="switch-versions-in-a-custom-connection-manager-task-enumerator-or-log-provider"></a>カスタム接続マネージャー、タスク、列挙子、またはログ プロバイダーのバージョンを切り替える

カスタム接続マネージャー、タスク、列挙子、またはログ プロバイダーでは、追加のロジックをダウン グレード、 **SaveToXML**メソッドです。

```csharp
public void SaveToXML(XmlDocument doc, IDTSInfoEvents events)
{
    if (TargetServerVersion == DTSTargetServerVersion.SQLServer2014)
    {
        // Add logic to downgrade from SQL Server 2016 to SQL Server 2014.
    }

    if (TargetServerVersion == DTSTargetServerVersion.SQLServer2012)
    {
         // Add logic to downgrade from SQL Server 2016 to SQL Server 2012.
    }
}
```

### <a name="switch-versions-in-a-custom-data-flow-component"></a>カスタム データ フロー コンポーネントのバージョンを切り替える

カスタム接続マネージャー、タスク、列挙子、またはログ プロバイダーでは、新たにダウン グレード ロジックを追加**PerformDowngrade**メソッドです。

```csharp
public override void PerformDowngrade(int pipelineVersion, DTSTargetServerVersion targetServerVersion)
{
    if (targetServerVersion == DTSTargetServerVersion.DTSTSV_SQLSERVER2014)
    {
        // Add logic to downgrade from SQL Server 2016 to SQL Server 2014.
        ComponentMetaData.Version = 8;
    }

    if (targetServerVersion == DTSTargetServerVersion.DTSTSV_SQLSERVER2012)
    {
          // Add logic to downgrade from SQL Server 2016 to SQL Server 2012.
        ComponentMetaData.Version = 6;
    }
}
```

## <a name="common-errors"></a>一般的なエラー

### <a name="invalidcastexception"></a>InvalidCastException

**エラー メッセージ。** 型のオブジェクトは COM をキャストできません。 'System.__ComObject' インターフェイスには、'Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100' を入力します。 次のエラーにより IID '{BE8C48A3-155B-4810-BA5C-BDF68A659E9E}' を持つインターフェイスの COM コンポーネント上での QueryInterface 呼び出しが失敗したため、この操作が失敗しました: インターフェイスがサポートされて (HRESULT からの例外: 0x80004002 (E_NOINTERFACE))。 (Microsoft.SqlServer.DTSPipelineWrap)。

**ソリューションです。** カスタム拡張機能は、Microsoft.SqlServer.DTSPipelineWrap など Microsoft.SqlServer.DTSRuntimeWrap SSIS の相互運用機能アセンブリを参照する場合の値を設定、**相互運用機能型の埋め込み**プロパティに * * False"です。

![相互運用機能型を埋め込み](../../integration-services/extending-packages-custom-objects/media/embed-interop-types.png)

### <a name="unable-to-load-some-types-when-target-version-is-sql-server-2012"></a>ターゲット バージョンが SQL Server 2012 の場合、一部の型を読み込めません。

この問題は、IErrorReportingService または IUserPromptService などの特定の種類に影響します。

**エラー メッセージ (例:)。** アセンブリから型 'Microsoft.DataWarehouse.Design.IErrorReportingService' を読み込むことができませんでした ' Microsoft.DataWarehouse, Version 13.0.0.0、カルチャを = = neutral, PublicKeyToken = 89845dcd8080cc91' です。

**回避策。** ターゲット バージョンが SQL Server 2012 の場合は、これらのインターフェイスではなく、メッセージ ボックスを使用します。

