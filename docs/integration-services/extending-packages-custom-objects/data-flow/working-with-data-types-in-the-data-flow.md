---
title: "データ フロー内のデータ型の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom data flow components [Integration Services], mapping data types
- data flow components [Integration Services], mapping data types
- data types [Integration Services], converting
ms.assetid: 941260d0-4ec3-4bf0-ab48-2b26733e6b24
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f020b16fd9609c64ed6a421c9c9f5e593d70276b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="working-with-data-types-in-the-data-flow"></a>データ フロー内のデータ型の処理
  Integration Services のカスタム データ フロー コンポーネント開発には、データ フロー バッファーにデータをコピーしたり、データ フロー バッファーからデータを取得したり、値を変換したりするなど、常にデータ型の処理が伴います。 このトピックでは、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] データ型の正しい選択と、それを扱うための適切なメソッドの使用について説明します。  
  
## <a name="inserting-data-into-the-data-flow"></a>データ フローへのデータの挿入  
 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>クラスは、一連の**設定**にバッファーの列、および対応する一連のデータをコピーするためのメソッド**取得**をバッファー列からデータを取得するメソッド。 次の表は、それぞれに使用する方法を示して[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]データ型。  
  
### <a name="set-methods-to-use-with-data-types"></a>データ型に対して使用する Set メソッド  
 次の表で、最初の列のデータ型と、対応を示します**設定**と**取得**メソッドです。  
  
|データ型|Set メソッド|Get メソッド|  
|---------------|----------------|----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BOOL>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetBoolean%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetBoolean%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BYTES>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetBytes%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetBytes%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_CY>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDecimal%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDecimal%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DATE>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDateTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBDATE>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDate%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDate%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME2>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDateTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP2>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDateTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMPOFFSET>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTimeOffset%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDateTimeOffset%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DECIMAL>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDecimal%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDecimal%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_FILETIME>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDateTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_GUID>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetGuid%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetGuid%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I1>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetSByte%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetSByte%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I2>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt16%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetInt16%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I4>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt32%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetInt32%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I8>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt64%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetInt64%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_IMAGE>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>または<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetBlobData%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NTEXT>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>または<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetBlobData%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NULL>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetNull%2A>|ない**取得**メソッドには、このデータ型に適用します。|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NUMERIC>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDecimal%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDecimal%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R4>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetSingle%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetSingle%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R8>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDouble%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDouble%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_STR>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetString%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetString%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_TEXT>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>または<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetBlobData%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI1>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetByte%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetByte%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI2>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt16%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetUInt16%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI4>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt32%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetUInt32%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI8>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt64%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetUInt64%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetString%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetString%2A>|  
  
### <a name="data-types-to-use-with-the-set-methods"></a>Set メソッドで使用するデータ型  
  
|Set メソッド|データ型|  
|----------------|---------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>または<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_IMAGE>、<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NTEXT>、または <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_TEXT>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetBoolean%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BOOL>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetByte%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI1>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetBytes%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BYTES>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDate%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBDATE>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTime%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DATE>, <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>, <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP2>, or<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_FILETIME>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTimeOffset%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMPOFFSET>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDecimal%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_CY>、<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DECIMAL>、または <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NUMERIC>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDouble%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R8>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetGuid%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_GUID>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt16%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I2>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt32%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I4>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt64%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I8>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetNull%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NULL>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetSByte%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I1>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetSingle%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R4>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetString%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_STR>または<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetTime%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME>または<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME2>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt16%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI2>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt32%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI4>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt64%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI8>|  
  
## <a name="mapping-data-types-in-the-data-flow"></a>データ フローでのデータ型のマッピング  
 変換のソースからデータを変換先に移動中に、データ フロー コンポーネント必要がある場合がありますデータ型変換の間、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]で定義された型、<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType>列挙体をマネージ データ型の[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]で定義されている、**システム**名前空間。 また、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] データ型をマネージ型に変換する前に、別の型への変換が必要になる場合もあります。  
  
> [!NOTE]  
>  既定では C:\Program files \microsoft SQL Server\130\DTS\MappingFiles にインストールされている XML 形式のマッピング ファイルは、このトピックで説明するデータ型マッピングには無関係です。 これらのファイルは、データ型をあるデータベース バージョンまたはシステムから別のデータベース バージョンまたはシステムにマップ ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から Oracle へのマッピングなど) したものであり、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインポートおよびエクスポート ウィザードでのみ使用されます。 これらのマッピング ファイルの詳細については、次を参照してください。 [SQL Server インポートおよびエクスポート ウィザード](~/integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md)です。  
  
### <a name="mapping-between-integration-services-and-managed-data-types"></a>Integration Services とマネージ データ型とのマッピング  
 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> メソッドおよび <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A> メソッドは、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のデータ型をマネージ データ型にマップします。  
  
> [!CAUTION]  
>  開発者が <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> クラスのこれらのメソッドを使用する際には注意が必要です。また、カスタム コンポーネントの固有の要件により適した独自のデータ型マッピング メソッドのコーディングが必要になる場合もあります。 既存のメソッドでは、数値有効桁数や小数点以下桁数が考慮されていません。また、他のプロパティは、データ型そのものに密接に関連します。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] の将来のバージョンでは、これらのメソッドが変更または削除されたり、メソッドが実行するマッピングが変更されたりする可能性があります。  
  
 次の表に、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> メソッドおよび <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A> メソッドで、各種の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] データ型がどのようにマネージ データ型にマップされるかを示します。  
  
|Integration Services データ型|マップ先のマネージ データ型|  
|------------------------------------|------------------------------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|System.String|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BYTES>|System.Byte の配列|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|System.DateTime|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP2>|System.DateTime|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMPOFFSET>|System.DateTimeOffset|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBDATE>|System.DateTime|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME>|System.TimeSpan|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME2>|System.TimeSpan|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DATE>|System.DateTime|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_FILETIME>|System.DateTime|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NUMERIC>|System.Decimal|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_GUID>|System.Guid|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I1>|System.SByte|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I2>|System.Int16|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I4>|System.Int32|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I8>|System.Int64|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BOOL>|System.Boolean|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R4>|System.Single|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R8>|System.Double|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI1>|System.Byte|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI2>|System.UInt16|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI4>|System.UInt32|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI8>|System.UInt64|  
  
### <a name="mapping-integration-services-data-types-to-fit-managed-data-types"></a>Integration Services データ型から適合マネージ データ型へのマッピング  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] データ型をマネージ型に変換する前に、データ フロー コンポーネントによる別の型への変換が必要になる場合もあります。 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>メソッド クラス マップ[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]を他のデータ型[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]を使用してデータ型にマップすることができますをマネージ データ型、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>メソッドです。  
  
> [!CAUTION]  
>  開発者が <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> クラスのこれらのメソッドを使用する際には注意が必要です。また、カスタム コンポーネントの固有の要件により適した独自のデータ型マッピング メソッドのコーディングが必要になる場合もあります。 既存のメソッドでは、数値有効桁数や小数点以下桁数が考慮されていません。また、他のプロパティは、データ型そのものに密接に関連します。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] の将来のバージョンでは、これらのメソッドが変更または削除されたり、メソッドが実行するマッピングが変更されたりする可能性があります。  
  
 次の表に、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A> メソッドで、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] データ型がどのように他の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] データ型にマップされるかを示します。  
  
|元の Integration Services データ型|マップ先の Integration Services データ型|  
|---------------------------------------------|-------------------------------------------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DECIMAL>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NUMERIC>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_CY>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NUMERIC>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DATE>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBDATE>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_FILETIME>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP2>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME2>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BOOL>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I4>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_TEXT>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NTEXT>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_STR>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_IMAGE>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BYTES>|  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A> メソッドでは、DT_DBTIMESTAMPOFFSET データ型の値が返されず、<xref:Microsoft.SqlServer.Dts.Pipeline.UnsupportedBufferDataTypeException> が発生します。 DT_DBTIMESTAMPOFFSET データ型は、マネージ データ型にマップできる、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のいずれかの日付/時刻データ型に変換する必要があります。 マネージ データ型にマップできる [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 日付/時刻データ型の一覧については、前のセクション「Integration Services とマネージ データ型とのマッピング」の表を参照してください。 データ型に変換する方法については、次を参照してください。 [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>   
 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>   
 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>   
 [Integration Services のデータ型](../../../integration-services/data-flow/integration-services-data-types.md)  
  
  
