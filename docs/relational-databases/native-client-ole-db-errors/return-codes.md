---
title: "リターン コードの |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-errors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- SQL Server Native Client OLE DB provider, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
ms.assetid: 7f7457e9-fce4-400c-82e5-ee02e9e811c6
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b76f5b35933a5455b6bba82fba818cbdba29d449
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="return-codes"></a>リターン コード
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  最も基本的なレベルでは、メンバー関数は成功するか失敗するかのどちらかです。 それよりもやや詳細なレベルでは、関数は成功しても、その成功はアプリケーション開発者が意図した状態ではない場合があります。  
  
 OLE DB のリターン コードの詳細については、次を参照してください。[リターン コード (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=101631)です。  
  
 ときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのメンバー関数が S_OK、その関数は成功を返します。  
  
 ときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのメンバー関数が S_OK を返さないことで、OLE/COM HRESULT をアンパックする FAILED マクロと IS_ERROR マクロは、全体的な成功または関数の失敗を判断できます。  
  
 FAILED または IS_ERROR が TRUE を返した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーがメンバー関数の実行が失敗したことを保証します。 FAILED または IS_ERROR が FALSE と、HRESULT、それを返す場合も、S_OK が等しくない、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーがある意味で、関数が成功したことを保証します。 コンシューマーからこの「成功した場合に情報を含む」を返す詳細の情報を取得できます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのエラー インターフェイスです。 また、関数 (、FAILED マクロに TRUE を返します) が失敗した明確にする場合、拡張エラー情報を表示から、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのエラー インターフェイスです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーのコンシューマーは、DB_S_ERRORSOCCURRED により成功が情報"HRESULT 戻り値をよく発生します。 通常、DB_S_ERRORSOCCURRED を返すメンバー関数では、コンシューマーに状態値を提供するパラメーターが 1 つ以上定義されています。 コンシューマーは状態値パラメーターに返される情報以外のエラー情報を取得できない場合があるので、状態値が提供された場合にこの値を取得できるアプリケーション ロジックを実装することをお勧めします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのメンバー関数は、成功コード S_FALSE を返しません。 すべて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーのメンバー関数は常に成功を示す S_OK を返します。  
  
## <a name="see-also"></a>参照  
 [エラー](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
