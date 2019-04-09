---
title: 如何：创建开发期间使用的临时证书
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: d45f18b0b8fe4e0cc9667091e166c80691faa2d4
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921320"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>如何：创建开发期间使用的临时证书

开发时的安全服务或使用 Windows Communication Foundation (WCF) 客户端，它通常是需要提供要用作凭据的 X.509 证书。 该证书通常是证书链的一部分，在计算机的受信任的根证书颁发机构存储区中可找到根证书颁发机构。 拥有一个证书链，使您可以限定一组证书，其中根证书颁发机构通常来自于您的组织或业务单元。 若要在开发时模拟此情况，请创建两个证书以满足安全要求。 第一个证书是自签名证书，放置在受信任的根证书颁发机构存储区中；第二个证书是从第一个证书创建的，放置在本地计算机位置的个人存储区中或当前用户位置的个人存储区中。 本主题将指导完成创建使用 Powershell 这两个证书的步骤[New-selfsignedcertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet。

> [!IMPORTANT]
> 仅用于测试目的提供 New-selfsignedcertificate cmdlet 生成的证书。 部署服务或客户程序时，请确保使用证书颁发机构提供的适当证书。 这可能是从你的组织中的 Windows Server 证书服务器，或第三方。
>
> 默认情况下[New-selfsignedcertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet 创建的是自签名证书和这些证书将不安全。 将自签名的证书放入受信任的根证书颁发机构存储区，可创建更紧密地模拟你的部署环境的开发环境。

 有关创建和使用证书的详细信息，请参阅[Working with Certificates](working-with-certificates.md)。 有关使用证书作为凭据的详细信息，请参阅[保护服务和客户端](securing-services-and-clients.md)。 有关使用 Microsoft Authenticode 技术的教程，请参阅 [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919)（Authenticode 概述和教程）。

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>创建一个自签名根证书颁发机构证书并导出私钥

以下命令创建一个自签名的证书的主题名称为"RootCA"当前用户个人存储区中。

```powershell
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```

我们需要将证书导出到 PFX 文件，以便可以导入到其中需要在后面的步骤。 时使用私钥导出的证书，需要密码以对其进行保护。 我们将密码存入`SecureString`，并使用[Export-pfxcertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet 将证书导出到 PFX 文件关联的私钥。 我们还将只需公共证书保存到 CRT 文件使用[导出证书](/powershell/module/pkiclient/export-certificate)cmdlet。

```powershell
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>创建一个由根证书颁发机构证书签名的新证书

以下命令将创建由签名的证书`RootCA`使用者名称为"SignedByRootCA"使用颁发者的私钥。

```powershell
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

同样，我们将保存的签名的证书使用私钥到 PFX 文件，并只是到 CRT 文件的公共密钥。

```powershell
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>在受信任的根证书颁发机构存储区中安装证书

创建自签名证书后，您可以将它安装到受信任的根证书颁发机构存储区中。 任何使用该证书签名的证书在此处都受计算机的信任。 为此，当您不再需要该证书时可立即将它从存储区中删除。 当您删除此根证书颁发机构证书时，则由它签名的所有其他证书将成为未经授权的。 根证书颁发机构证书只是一种机制，必要时可限定一组证书。 例如，在对等应用程序中，通常不需要根证书颁发机构，因为您只信任由对方提供的证书的个体标识。

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>在受信任的根证书颁发机构中安装自签名证书

1. 打开证书管理单元。 有关详细信息，请参阅[如何：使用 MMC 管理单元查看证书](how-to-view-certificates-with-the-mmc-snap-in.md)。

2. 打开要存储证书的文件夹， **“本地计算机”** 或 **“当前用户”**。

3. 打开 **“受信任的根证书颁发机构”** 文件夹。

4. 右击 **“证书”** 文件夹，再单击 **“所有任务”**，然后单击 **“导入”**。

5. 按照屏幕向导说明 RootCA.pfx 导入的存储。

## <a name="using-certificates-with-wcf"></a>使用证书与 WCF

一旦安装了临时证书，就可以使用这些证书开发指定证书作为客户端凭据类型的 WCF 解决方案。 例如，下面的 XML 配置指定消息安全模式，并指定证书作为客户端凭据类型。

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>指定证书作为客户端凭据类型

1. 在服务的配置文件中，使用下面的 XML 将安全模式设置为消息，并将客户端凭据类型设置为证书。

    ```xml
    <bindings>
      <wsHttpBinding>
        <binding name="CertificateForClient">
          <security>
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

2. 在客户端的配置文件，使用下面的 XML 指定的证书位于用户的存储，以及可以通过搜索"CohoWinery。"的值在 SubjectName 字段中找到

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="CertForClient">
          <clientCredentials>
            <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

有关在 WCF 中使用证书的详细信息，请参阅 [Working with Certificates](working-with-certificates.md)。

## <a name="net-framework-security"></a>.NET Framework 安全性

请确保通过右击证书，再单击 **“删除”** ，从 **“受信任的根证书颁发机构”** 和 **“个人”** 文件夹中删除所有临时根证书颁发机构证书。

## <a name="see-also"></a>请参阅

- [使用证书](working-with-certificates.md)
- [如何：使用 MMC 管理单元查看证书](how-to-view-certificates-with-the-mmc-snap-in.md)
- [保护服务和客户端的安全](securing-services-and-clients.md)
