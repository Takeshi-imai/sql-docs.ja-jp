---
title: "GetDatabaseVersionDisplayName メソッド (WMI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
caps.latest.revision: 15
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b4743439f2edf3f3cfb253aa981af83350f5aff7
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="configurationsetting-method---getdatabaseversiondisplayname"></a>GetDatabaseVersionDisplayName ConfigurationSetting メソッド
  指定したレポート サーバー データベースのバージョン文字列の表示名を取得します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub GetDatabaseVersionDisplayName(Version As String, DisplayName As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetDatabaseVersionDisplayName(string Version, string DisplayName, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *バージョン*  
 レポート サーバー データベースのバージョン文字列を含む文字列。  
  
 *DisplayName*  
 [out] 指定したバージョンに対応する表示名を含む文字列。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="remarks"></a>解説  
 次の表に、データベース バージョンと表示文字列のマッピングを示します。  
  
|**リリース**|**バージョン**|**表示名**|  
|-----------------|-----------------|----------------------|  
|RS 2005 SP2|@DBVersion'C.0.8.54' を =|SQL Server 2005 SP2|  
|RS 2005 SP1|@DBVersion'C.0.8.43' を =|SQL Server 2005 SP1|  
|RS 2005 RTM|@DBVersion'C.0.8.40' を =|SQL Server 2005|  
|RS 2000 SP2|@DBVersion'C.0.6.54' を =|SQL Server 2000 SP2|  
|RS 2000 SP1|@DBVersion'C.0.6.51' を =|SQL Server 2000 SP1|  
|RS 2000 RTM|@DBVersion'C.0.6.43' を =|SQL Server 2000|  
|修正プログラム||最も近い適用可能なバージョン|  
  
 *2000 より前の* Version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、HRESULT として ACT_E_BAD_VERSION が返されます。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  