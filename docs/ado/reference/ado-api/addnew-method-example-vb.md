---
title: "AddNew メソッドの例 (VB) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- AddNew method [ADO], Visual Basic example
ms.assetid: d439e097-65f3-471d-8799-5a1263beb3c1
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a9ff526eadc0d21407223841c59c424548e0f264
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="addnew-method-example-vb"></a>AddNew メソッドの例 (VB)
この例では、 [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)メソッドを指定した名前の新しいレコードを作成します。  
  
```  
'BeginAddNewVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset and connection variables  
    Dim Cnxn As ADODB.Connection  
    Dim rstEmployees As ADODB.Recordset  
    Dim strCnxn As String  
    Dim strSQL As String  
     'record variables  
    Dim strID As String  
    Dim strFirstName As String  
    Dim strLastName As String  
    Dim blnRecordAdded As Boolean  
  
    ' Open a connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Northwind';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open Employees Table with a cursor that allows updates  
    Set rstEmployees = New ADODB.Recordset  
    strSQL = "Employees"  
    rstEmployees.Open strSQL, strCnxn, adOpenKeyset, adLockOptimistic, adCmdTable  
  
    ' Get data from the user  
    strFirstName = Trim(InputBox("Enter first name:"))  
    strLastName = Trim(InputBox("Enter last name:"))  
  
    ' Proceed only if the user actually entered something  
    ' for both the first and last names  
    If strFirstName <> "" And strLastName <> "" Then  
  
        rstEmployees.AddNew  
        rstEmployees!firstname = strFirstName  
        rstEmployees!LastName = strLastName  
        rstEmployees.Update  
        blnRecordAdded = True  
  
        ' Show the newly added data  
        MsgBox "New record: " & rstEmployees!EmployeeId & " " & _  
        rstEmployees!firstname & " " & rstEmployees!LastName  
  
    Else  
        MsgBox "Please enter a first name and last name."  
    End If  
  
    ' Delete the new record because this is a demonstration  
    Cnxn.Execute "DELETE FROM Employees WHERE EmployeeID = '" & strID & "'"  
  
    ' clean up  
    rstEmployees.Close  
    Cnxn.Close  
    Set rstEmployees = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
   ' clean up  
    If Not rstEmployees Is Nothing Then  
        If rstEmployees.State = adStateOpen Then rstEmployees.Close  
    End If  
    Set rstEmployees = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndAddNewVB  
```  
  
## <a name="see-also"></a>参照  
 [AddNew メソッド (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
