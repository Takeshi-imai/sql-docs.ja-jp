---
title: "LocalDBGetVersionInfo 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- LocalDBGetVersionInfo
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e3fb6ab670f626cb629a1ba301cab4b51c9a2c56
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="localdbgetversioninfo-function"></a>LocalDBGetVersionInfo 関数
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
指定した SQL Server Express LocalDB バージョンの情報を返します。たとえば、存在するかどうか、LocalDB 完全バージョン番号 (ビルド番号やリリース番号を含む) などです。  
  
 形式で返される情報、**構造体**という**LocalDBVersionInfo**、次の定義を持ちます。  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 **ヘッダー ファイル:** sqlncli.h  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a>パラメーター  
 *wszVersionName*  
 [入力] LocalDB バージョンの名前。  
  
 *pVersionInfo*  
 [出力] LocalDB バージョンについての情報を格納するバッファー。  
  
 *dwVersionInfoSize*  
 [入力]サイズを保持する、 *VersionInfo*バッファー。  
  
## <a name="returns"></a>返します。  
 S_OK  
 関数が正常に実行されました。  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB は、コンピューターにインストールされていません。  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 指定した 1 つまたは複数の入力パラメーターが無効です。  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-version.md)  
 指定された LocalDB バージョンが存在しません。  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 予期しないエラーが発生しました。 詳細をイベント ログで確認してください。  
  
## <a name="details"></a>詳細  
 導入根拠、**構造体**サイズ引数 (*lpVersionInfoSize*) を返す別のバージョンの API を有効にするのには、 **LocalDBVersionInfostruct**、効果的に上位および下位互換性を有効にします。  
  
 場合、**構造体**サイズ引数 (*lpVersionInfoSize*) の既知のバージョンのサイズと一致する、 **LocalDBVersionInfostruct**、そのバージョンの**構造体**が返されます。 それ以外の場合、LOCALDB_ERROR_INVALID_PARAMETER が返されます。  
  
 典型的な例**LocalDBGetVersionInfo** API の使用率が次のように検索します。  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L”11.0”, &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a>解説  
 LocalDB API を使用するコード サンプルは、次を参照してください。 [SQL Server Express LocalDB リファレンス](../../relational-databases/sql-server-express-localdb-reference.md)です。  
  
## <a name="see-also"></a>参照  
 [SQL Server Express LocalDB ヘッダーとバージョン情報](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
