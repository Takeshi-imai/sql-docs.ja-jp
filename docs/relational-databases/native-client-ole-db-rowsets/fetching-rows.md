---
title: "行のフェッチ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- IRowset interface
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 5e6dbe36-b682-464d-adfa-8e886f9bd452
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9aa63737e286f8890a9ee454983428ef90e61a31
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="fetching-rows"></a>行のフェッチ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **IRowset**インターフェイスは、行セットの基本インターフェイスです。 **IRowset**インターフェイスには、行を順番にフェッチ、これらの行からデータを取得する行を管理するためのメソッドが用意されています。 コンシューマーでメソッドを使用して**IRowset**すべての行セットの基本的な操作です。 基本的な操作には、行のフェッチと解放、列値の取得などがあります。  
  
 使用して、行セットの機能を決定する通常の最初の手順では、コンシューマーが行セットに対するインターフェイス ポインターを取得する際、 **irowsetinfo:**メソッドです。 このメソッドにより、行セットが公開しているインターフェイスに関する情報に加えて、個別のインターフェイスとしては提供されない行セットの機能に関する情報も返されます。このような行セットの情報には、アクティブ行の最大数や、保留中の更新を同時に含むことができる行数などが含まれています。  
  
 次に、コンシューマーは、行セット内の列の特性、つまりメタデータを調査します。 これを使用、 **IColumnsInfo**簡易列情報メソッドまたは**IColumnsRowset**メソッド拡張列情報です。 **GetColumnInfo**メソッドは、次の情報を返します。  
  
-   結果セット内の列数。  
  
-   DBCOLUMNINFO 構造体の配列。列ごとに 1 つの構造体があります。  
  
     構造体の順序は、行セット内で列が表示される順序です。 各 DBCOLUMNINFO 構造体には、列名、列の序数、列の値の最大長、列のデータ型、有効桁数、長さなど、列のメタデータが格納されます。  
  
-   1 つのアロケーション ブロック内にあるすべての文字列値に関するストレージへのポインター。  
  
 コンシューマーは必要な列を、メタデータから判断するか、行セットを生成したテキスト コマンドに基づいて判断します。 によって返される列の情報の順序付けから、必要な列の序数が決まります**IColumnsInfo**またはによって返される列のメタデータ行セット内の序数**IColumnsRowset**です。  
  
 **IColumnsInfo**と**IColumnsRowset**インターフェイスは、行セット内の列に関する情報を抽出するために使用します。 **IColumnsInfo**インターフェイスが限られた情報を返しますが**IColumnsRowset**すべてのメタデータを提供します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0 以前では、省略可能なメタデータ列 DBCOLUMN_COMPUTEMODE は、によって返される**icolumnsinfo::getcolumnsinfo** (列かどうかを示す値ではなく、DBSTATUS_S_ISNULL を返します計算された) 基になる列が計算列かどうかを確認できないためです。  
  
 序数を使用して、列へのバインドを指定します。 バインドとは、コンシューマーの構造体の要素を列に関連付ける 1 つの構造体です。 バインドでは、列のデータ値、長さ、および状態値をバインドできます。  
  
 バインドのセットは、アクセサーでまとめて収集されます。 これを使用して作成される、 **iaccessor::createaccessor**メソッドです。 アクセサーには複数のバインドを含めることができるので、複数の列のデータを 1 回の呼び出しで取得または設定できます。 コンシューマーは、アプリケーションのさまざまな部分によって異なる使用パターンに合わせて、複数のアクセサーを作成できます。 行セットが存在する間は、アクセサーを作成および解放できます。  
  
 データベースから行をフェッチするコンシューマー、メソッドを呼び出しなど**irowset::getnextrows**または**irowsetlocate::getrowsat**です。 これらのフェッチ操作により、サーバーの行データがプロバイダーの行バッファーに格納されます。 コンシューマーは、プロバイダーの行バッファーに直接アクセスできません。 コンシューマーは**irowset::getdata**プロバイダーのバッファーからデータをコンシューマーのバッファーにコピーして**irowsetchange::setdata**データ変更をコンシューマー バッファーからプロバイダーのバッファーにコピーします。  
  
 コンシューマーは、 **GetData**メソッドしするには、行、アクセサーのハンドルとコンシューマーが割り当てたバッファーへのポインター、ハンドルを渡します。 **GetData**データに変換され、アクセサーの作成に使用するバインディングで指定されている列が返されます。 コンシューマーが呼び出すことができます**GetData**行の場合、1 つ以上の時間がさまざまなアクセサーやバッファーしたがってコンシューマーを使用して、同じデータの複数のコピーを取得できます。  
  
 可変長列のデータは、さまざまな方法で処理できます。 最初に、このような列をコンシューマーの構造体の有限部分にバインドできます。 この場合、データの長さがバッファー長を超えると切り捨てが発生します。 コンシューマーは状態 DBSTATUS_S_TRUNCATED を確認することで、切り捨てが発生したかどうかを判断できます。 返される長さは、常に、実際のバイト単位の長さなので、切り捨てられたデータ量も判断できます。  
  
 コンシューマーには、フェッチまたは行の更新が完了したら、解放、 **ReleaseRows**メソッドです。 これにより、行セット内の行のコピーからリソースが解放され、新しい行の空き領域が確保されます。 その後、行のフェッチや作成、行データへのアクセスといったサイクルを繰り返すことができます。  
  
 コンシューマーは、完了すると、行セットが、呼び出し、 **iaccessor::releaseaccessor**アクセサーを解放します。 呼び出す、 **iunknown::release**行セットを解放する、行セットによって公開されているすべてのインターフェイスのメソッドです。 行セットが解放されると、コンシューマーが保持している残りの行やアクセサーも強制的に解放されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [次のフェッチ位置](../../relational-databases/native-client-ole-db-rowsets/fetching-rows-next-fetch-position.md)  
  
## <a name="see-also"></a>参照  
 [行セット](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
