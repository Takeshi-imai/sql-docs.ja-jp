---
title: "RemoveURL メソッド (WMI MSReportServer_ConfigurationSetting) |Microsoft ドキュメント"
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
- RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b47933be28aae96673ca6c3b28410874c01394dc
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="configurationsetting-method---removeurl"></a>RemoveURL ConfigurationSetting メソッド
  レポート サーバー用に予約されている URL を削除します。 削除の対象となる URL が複数ある場合は、この API を 1 つずつ呼び出して URL を削除する必要があります。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *アプリケーション*  
 予約を削除する対象のアプリケーションの名前。  
  
 *URLString*  
 予約する URL。  
  
 *lcid*  
 返されるエラー メッセージに使用するロケール。  
  
 *[エラー]*  
 [out] 発生したエラーの説明。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。  
  
## <a name="remarks"></a>解説  
 *UrlString* には、仮想ディレクトリの名前が含まれていません。その目的では、[SetVirtualDirectory Method (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setvirtualdirectory.md) メソッドが提供されます。  
  
 [ReserveURL](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-reserveurl.md) メソッドを呼び出す前に、*Application* パラメーターの VirtualDirectory 構成プロパティの値を指定する必要があります。 [SetVirtualDirectory Method (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setvirtualdirectory.md) メソッドを利用し、VirtualDirectory プロパティをせっていします。  
  
 SSL 証明書が [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で準備されていて、他の URL でその証明書を使用する必要がない場合、その SSL 証明書は削除されます。  
  
 このメソッドにより、すべての非構成アプリケーション ドメインで強制力の高いリサイクル処理が実行され、その処理中にそれらのドメインは停止します。アプリケーション ドメインは、この処理の完了後に再起動します。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  