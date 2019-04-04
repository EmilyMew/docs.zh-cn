---
title: 如何：使用用户名和密码进行身份验证
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: f6939659249ea40e97f340771017d0587ec6a08f
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412261"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>如何：使用用户名和密码进行身份验证

本主题演示如何启用 Windows Communication Foundation (WCF) 服务进行身份验证的客户端使用 Windows 域用户名和密码。 它假定您有一个正在工作的自承载 WCF 服务。 有关创建基本自承载的 WCF 服务，请参阅示例[入门教程](../../../../docs/framework/wcf/getting-started-tutorial.md)。 本主题假定在代码中配置服务。 如果你想要看到的配置类似服务使用配置文件示例请参阅[用户名消息安全](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 要配置服务以使用 Windows 域用户名和密码对其客户端进行身份验证，请使用 <xref:System.ServiceModel.WSHttpBinding>，并将其 `Security.Mode` 属性设置为 `Message`。 此外，您必须指定 X509 证书，该证书用于在将用户名和密码从客户端发送到服务时对它们进行加密。  
  
 在客户端上，您必须提示用户输入用户名和密码，并指定用户在 WCF 客户端代理上的凭据。  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>若要配置使用 Windows 域用户名和密码进行身份验证的 WCF 服务
  
1.  创建 <xref:System.ServiceModel.WSHttpBinding> 的实例，将绑定的安全模式设置为 <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>，将绑定的 `ClientCredentialType` 设置为 <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>，并使用配置的绑定将服务终结点添加到服务主机，如下面的代码中所示：  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  指定用于对通过网络发送的用户名和密码信息进行加密的服务器证书。 此代码应紧跟在上面的代码之后。 下面的示例使用的 setup.bat 文件创建的证书[用户名消息安全](../../../../docs/framework/wcf/samples/message-security-user-name.md)示例：  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     您可以使用您自己的证书，只需修改代码以引用您的证书。 有关创建和使用证书的详细信息请参阅[Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。 确保证书在本地计算机的受信任人证书存储区中。 您可以执行此操作通过运行 mmc.exe 并选择**文件**，**添加/删除管理单元中...** 菜单项。 在中**添加或删除管理单元**对话框中，选择**管理单元中的证书**然后单击**添加**。 在证书管理单元对话框中选择**计算机帐户**。 默认情况下，从消息安全用户名称示例生成的证书将位于个人/证书文件夹中。  它将列为"localhost"颁发给在 MMC 窗口中的列。 拖放到到证书**受信任的人员**文件夹。 这将允许 WCF 在执行身份验证时，将证书视为受信任的证书。  
  
## <a name="to-call-the-service-passing-username-and-password"></a>调用服务传递用户名和密码  
  
1.  客户端应用程序必须提示用户输入其用户名和密码。 下面的代码要求用户输入用户名和密码。  
  
    > [!WARNING]
    >  此代码不应在生产中使用，因为密码在输入时将显示出来。  
  
    ```  
    public static void GetPassword(out string username, out string password)  
            {  
                Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");  
                Console.WriteLine("   Enter username:");  
                username = Console.ReadLine();  
                Console.WriteLine("   Enter password:");  
                password = Console.ReadLine();             
                return;  
            }  
    ```  
  
2.  创建客户端代理的一个实例，用于指定客户端的证书，如下面的代码所示：  
  
    ```  
    string username;  
    string password;  
  
    // Instantiate the proxy  
    Service1Client proxy = new Service1Client();  
  
    // Prompt the user for username & password  
    GetPassword(out username, out password);  
  
    // Set the user’s credentials on the proxy  
    proxy.ClientCredentials.UserName.UserName = username;  
    proxy.ClientCredentials.UserName.Password = password;  
  
    // Treat the test certificate as trusted  
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;  
    // Call the service operation using the proxy  
    ```  
  
## <a name="see-also"></a>请参阅
- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [使用基本身份验证的传输安全性](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)
- [分布式应用程序安全](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
