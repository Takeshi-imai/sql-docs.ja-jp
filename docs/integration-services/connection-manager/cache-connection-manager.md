---
title: "キャッシュ接続マネージャー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Cache connection manager
ms.assetid: bdc92038-3720-4795-8a5c-79b963f2c952
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 871402636ad6d3c4ba96277aa23ac95af5a801e7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="cache-connection-manager"></a>キャッシュ接続マネージャー
  キャッシュ接続マネージャーでは、キャッシュ変換またはキャッシュ ファイル (.caw) からデータを読み取り、そのデータをキャッシュ ファイルに保存できます。 キャッシュ ファイルを使用するようにキャッシュ接続マネージャーを構成したかどうかに関係なく、データは常にメモリに格納されます。  
  
 キャッシュ変換を使用して、データ フロー内の接続されているデータ ソースのデータをキャッシュ接続マネージャーに書き込みます。 パッケージ内の参照変換は、データに対する参照を実行します。  
  
> [!NOTE]  
>  キャッシュ接続マネージャーでは、バイナリ ラージ オブジェクト (BLOB) データ型 DT_TEXT、DT_NTEXT、および DT_IMAGE はサポートされません。 参照データセットに BLOB データ型が含まれている場合、パッケージを実行するとコンポーネントは失敗します。 **[キャッシュ接続マネージャー エディター]** を使用して、列のデータ型を変更できます。 詳細については、「 [キャッシュ接続マネージャー エディター](cache-connection-manager-editor.md)」をご覧ください。  
  
> [!NOTE]  
>  パッケージの保護レベルは、キャッシュ ファイルに適用されません。 キャッシュ ファイルに機密情報が含まれている場合は、アクセス制御リスト (ACL) を使用して、ファイルを格納している場所またはフォルダーへのアクセスを制限します。 特定のアカウントに対してのみアクセスを有効にする必要があります。 詳細については、「 [パッケージで使用されるファイルへのアクセス](../../integration-services/security/security-overview-integration-services.md#files)」を参照してください。  
  
## <a name="configuration-of-the-cache-connection-manager"></a>キャッシュ接続マネージャーの構成  
 キャッシュ接続マネージャーは、次の方法で構成できます。  
  
-   キャッシュ ファイルを使用するかどうかを示します。  
  
     キャッシュ ファイルを使用するようにキャッシュ接続マネージャーを構成すると、接続マネージャーは、次のいずれかの処理を実行します。  
  
    -   データ フロー内のデータ ソースからキャッシュ接続マネージャーにデータが書き込まれるようにキャッシュ変換が構成されている場合は、データをファイルに保存します。  
  
    -   キャッシュ ファイルからデータを読み取ります。  
  
     詳しくは、「 [Cache Transform](../../integration-services/data-flow/transformations/cache-transform.md)」をご覧ください。  
  
-   キャッシュに格納されている列のメタデータを変更します。  
  
-   式を使用して ConnectionString プロパティを設定し、実行時にキャッシュ ファイル名を更新します。 詳細については、「 [パッケージでプロパティ式を使用する](../../integration-services/expressions/use-property-expressions-in-packages.md)」を参照してください。  
  
 プロパティを設定するには [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] デザイナーで設定できるプロパティの詳細については、「 [[キャッシュ接続マネージャー エディター] ダイアログ ボックス](../../integration-services/connection-manager/cache-connection-manager-editor.md)」を参照してください。  
  
 接続マネージャーをプログラムから構成する方法については、次を参照してください。<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>と[プログラムで接続を追加する](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)です。  
  
## <a name="related-tasks"></a>関連タスク  
 [キャッシュ接続マネージャーを使用してフル キャッシュ モードで参照変換を実装します。](lookup-transformation-full-cache-mode-cache-connection-manager.md)  
  
  