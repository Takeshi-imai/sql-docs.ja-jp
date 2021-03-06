---
title: "スクリプト タスクによる HTML メール メッセージの送信 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-task-examples
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Send Mail task [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], HTML mail message
ms.assetid: dd2b1eef-b04f-4946-87ab-7bc56bb525ce
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b153c58fffdf4ac0833c683555ba25d4bf2737b6
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="sending-an-html-mail-message-with-the-script-task"></a>スクリプト タスクによる HTML メール メッセージの送信
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の SendMail タスクでは、プレーン テキスト形式のメール メッセージのみがサポートされています。 ただし、.NET Framework のスクリプト タスクとメール機能を使用して、HTML メール メッセージを簡単に送信できます。  
  
> [!NOTE]  
>  複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。 詳細については、「 [カスタム タスクの開発](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。  
  
## <a name="description"></a>Description  
 次の例では、**System.Net.Mail** 名前空間を使用して、HTML メール メッセージを構成および送信します。 スクリプトは、電子メールの宛先、差出人、件名、および本文をパッケージ変数から取得し、これらを使用して新しい **MailMessage** を作成します。また、その **IsBodyHtml** プロパティに **True** を設定します。 次に、別のパッケージ変数から SMTP サーバー名を取得し、**System.Net.Mail.SmtpClient** のインスタンスを初期化し、そのインスタンスの **Send** メソッドを呼び出して HTML メッセージを送信します。 このサンプルでは、メッセージ送信機能をサブルーチンにカプセル化しているため、他のスクリプトで再利用できます。  
  
#### <a name="to-configure-this-script-task-example-without-an-smtp-connection-manager"></a>このスクリプト タスクの例を SMTP 接続マネージャーを使用せずに構成するには  
  
1.  `HtmlEmailTo`、`HtmlEmailFrom`、および `HtmlEmailSubject` という名前の文字列変数を作成し、これらに適切な値を割り当てて、有効なテスト メッセージを用意します。  
  
2.  `HtmlEmailBody` という名前の文字列変数を作成し、HTML マークアップの文字列を割り当てます。 例 :  
  
    ```  
    <html><body><h1>Testing</h1><p>This is a <b>test</b> message.</p></body></html>  
    ```  
  
3.  `HtmlEmailServer` という名前の文字列変数を作成し、匿名発信メッセージを受け入れる、使用可能な SMTP サーバーの名前を割り当てます。  
  
4.  これらの 5 つすべての変数を、新しいスクリプト タスクの **ReadOnlyVariables** プロパティに割り当てます。  
  
5.  コードに **System.Net** および **System.Net.Mail** 名前空間をインポートします。  
  
 このトピックのサンプル コードでは、SMTP サーバー名をパッケージ変数から取得します。 ただし、SMTP 接続マネージャーを利用して接続情報をカプセル化し、コード内で接続マネージャーからサーバー名を抽出することもできます。 SMTP 接続マネージャーの <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> メソッドは、次の形式の文字列を返します。  
  
 `SmtpServer=smtphost;UseWindowsAuthentication=False;EnableSsl=False;`  
  
 **String.Split** メソッドを使用して、この引数リストをセミコロン (;) または等号 (=) で個々の文字列の配列に分割し、配列の 2 番目の引数 (subscript 1) をサーバー名として抽出することができます。  
  
#### <a name="to-configure-this-script-task-example-with-an-smtp-connection-manager"></a>このスクリプト タスクの例を SMTP 接続マネージャーを使用して構成するには  
  
1.  **ReadOnlyVariables** の一覧から `HtmlEmailServer` 変数を削除して、前に構成したスクリプト タスクを変更します。  
  
2.  サーバー名を取得する次のコード行を置き換えます。  
  
    ```  
    Dim smtpServer As String = _  
      Dts.Variables("HtmlEmailServer").Value.ToString  
    ```  
  
     次のコードを使用します。  
  
    ```  
    Dim smtpConnectionString As String = _  
      DirectCast(Dts.Connections("SMTP Connection Manager").AcquireConnection(Dts.Transaction), String)  
    Dim smtpServer As String = _  
      smtpConnectionString.Split(New Char() {"="c, ";"c})(1)  
    ```  
  
## <a name="code"></a>コード  
  
```vb  
Public Sub Main()  
  
  Dim htmlMessageFrom As String = _  
    Dts.Variables("HtmlEmailFrom").Value.ToString  
  Dim htmlMessageTo As String = _  
    Dts.Variables("HtmlEmailTo").Value.ToString  
  Dim htmlMessageSubject As String = _  
    Dts.Variables("HtmlEmailSubject").Value.ToString  
  Dim htmlMessageBody As String = _  
    Dts.Variables("HtmlEmailBody").Value.ToString  
  Dim smtpServer As String = _  
    Dts.Variables("HtmlEmailServer").Value.ToString  
  
  SendMailMessage( _  
      htmlMessageFrom, htmlMessageTo, _  
      htmlMessageSubject, htmlMessageBody, _  
      True, smtpServer)  
  
  Dts.TaskResult = ScriptResults.Success  
  
End Sub  
  
Private Sub SendMailMessage( _  
    ByVal From As String, ByVal SendTo As String,  _  
    ByVal Subject As String, ByVal Body As String, _  
    ByVal IsBodyHtml As Boolean, ByVal Server As String)  
  
  Dim htmlMessage As MailMessage  
  Dim mySmtpClient As SmtpClient  
  
  htmlMessage = New MailMessage( _  
    From, SendTo, Subject, Body)  
  htmlMessage.IsBodyHtml = IsBodyHtml  
  
  mySmtpClient = New SmtpClient(Server)  
  mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials  
  mySmtpClient.Send(htmlMessage)  
  
End Sub  
```  
  
```csharp  
public void Main()  
        {  
  
            string htmlMessageFrom = Dts.Variables["HtmlEmailFrom"].Value.ToString();  
            string htmlMessageTo = Dts.Variables["HtmlEmailTo"].Value.ToString();  
            string htmlMessageSubject = Dts.Variables["HtmlEmailSubject"].Value.ToString();  
            string htmlMessageBody = Dts.Variables["HtmlEmailBody"].Value.ToString();  
            string smtpServer = Dts.Variables["HtmlEmailServer"].Value.ToString();  
  
            SendMailMessage(htmlMessageFrom, htmlMessageTo, htmlMessageSubject, htmlMessageBody, true, smtpServer);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
        private void SendMailMessage(string From, string SendTo, string Subject, string Body, bool IsBodyHtml, string Server)  
        {  
  
            MailMessage htmlMessage;  
            SmtpClient mySmtpClient;  
  
            htmlMessage = new MailMessage(From, SendTo, Subject, Body);  
            htmlMessage.IsBodyHtml = IsBodyHtml;  
  
            mySmtpClient = new SmtpClient(Server);  
            mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials;  
            mySmtpClient.Send(htmlMessage);  
  
        }  
```  
  
## <a name="see-also"></a>参照  
 [メール送信タスク](../../integration-services/control-flow/send-mail-task.md)  
  
  
