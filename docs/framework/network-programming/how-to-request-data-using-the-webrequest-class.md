---
title: 如何：使用 WebRequest 类请求数据
ms.date: 03/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
ms.openlocfilehash: 1b71327d007e66cc217f6d69e11122c481e5118f
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634032"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>如何：使用 WebRequest 类请求数据
以下过程描述从服务器请求资源（如网页或文件）的步骤。 资源必须由 URI 标识。  
  
## <a name="to-request-data-from-a-host-server"></a>从主机服务器请求数据  
  
1.  通过使用资源 URI 调用 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 来创建 <xref:System.Net.WebRequest> 实例。 例如: 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/default.html");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/default.html")  
    ```  
  
    > [!NOTE]
    > .NET Framework 为以“http:”、“https:”、“ftp:”和“file:”开头的 URI 提供派生自 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 类的特定于协议的类。
    如果需要设置或读取特定于协议的属性，必须将 <xref:System.Net.WebRequest> 或 <xref:System.Net.WebResponse> 转换为特定于协议的对象类型。 有关详细信息，请参阅[对可插入协议进行编程](programming-pluggable-protocols.md)。 
  
2.  设置 `WebRequest` 对象中任何所需的属性值。 例如，若要启用身份验证，则将 <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> 属性设置为 <xref:System.Net.NetworkCredential> 类的实例：  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3.  通过调用 <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> 向服务器发送请求。 此方法返回包含服务器响应的对象。 返回的 <xref:System.Net.WebResponse> 对象的类型由请求的 URI 的方案决定。 例如:
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
4.  可以访问 `WebResponse` 对象的属性或将其强制转换为特定于协议的实例，以读取特定于协议的属性。 

    例如，要访问 <xref:System.Net.HttpWebResponse> 特定于 HTTP 的属性，请将 `WebResponse` 对象强制转换为 `HttpWebResponse` 引用。 以下代码示例演示如何显示与响应一起发送的特定于 HTTP 的 <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> 属性：
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  要获取包含由服务器发送的响应数据的流，请调用 <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> 方法。 例如:  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  从响应对象读取数据后，可以使用 <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> 方法关闭它，也可以使用 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法关闭响应流。 如果不关闭响应对象或流，则应用程序可能会耗尽服务器连接，并且无法处理其他请求。 因为 `WebResponse.Close` 方法在其关闭响应时调用 `Stream.Close`，所以不必在响应和流对象上调用 `Close`，尽管这样做没有坏处。 例如:
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>示例  

以下代码示例演示如何创建对 Web 服务器的请求并读取其响应中的数据：  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create(  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  

            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  

            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream();  
            // Open the stream by using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  

            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  

            // Clean up the response.  
            reader.Close();  
            response.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  

Namespace Examples.System.Net 

    Public Class WebRequestGetExample  

        Public Shared Sub Main()  

            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  

            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  

            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream by using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  

            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  

            ' Clean up the response.  
            reader.Close()  
            response.Close() 

        End Sub   

    End Class  
 
End Namespace  
```  
  
## <a name="see-also"></a>请参阅
- [创建 Internet 请求](creating-internet-requests.md)
- [在网络上使用流](using-streams-on-the-network.md)
- [通过代理访问 Internet](accessing-the-internet-through-a-proxy.md)
- [请求数据](requesting-data.md)
- [如何：使用 WebRequest 类发送数据](how-to-send-data-using-the-webrequest-class.md)
