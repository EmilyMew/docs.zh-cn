---
ms.openlocfilehash: d48519443aeee05617538cf2cc12bea49ad3e16d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761237"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>现在，当 .NET 无法处理证书时，不会引发 X509Certificate2.ToString(Boolean)

|   |   |
|---|---|
|详细信息|在 .NET Framework 4.5.2 及更早版本中，如果为详细参数传递了 <code>true</code>，并且安装了 .NET Framework 不支持的证书，则会引发此方法。 现在，该方法将取得成功，并返回省略证书无法访问部分的有效字符串。|
|建议|应更新任何依赖 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> 的代码，以希望返回的字符串会排除在某些情况下，API 之前曾引发的某些证书数据（例如公钥、私钥和扩展）。|
|范围|边缘|
|版本|4.6|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

