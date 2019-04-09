---
title: 根据服务元数据生成 WCF 客户端
ms.date: 03/30/2017
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
ms.openlocfilehash: 5cfbfc1e4be0003b3699f818212fbcd959f3ad91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078247"
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>根据服务元数据生成 WCF 客户端
本主题介绍如何使用 Svcutil.exe 中的各种开关，根据元数据文档生成客户端。  
  
 元数据文档可以位于持久性存储区中，也可以联机检索。 联机检索遵循 WS-MetadataExchange 协议或 Microsoft 发现 (DISCO) 协议。 Svcutil.exe 同时发出以下元数据请求以检索元数据：  
  
-   发往所提供地址的 WS-MetadataExchange (MEX) 请求。  
  
-   发往所提供地址的 MEX 请求，并追加了 `/mex`。  
  
-   DISCO 请求 (使用[DiscoveryClientProtocol](https://go.microsoft.com/fwlink/?LinkId=94777)从 ASP.NET Web 服务) 针对所提供地址。  
  
 Svcutil.exe 基于 Web 服务描述语言 (WSDL) 或从服务接收的策略文件生成客户端。 通过串联用户名称和生成的用户主体名称 (UPN)"\@"，然后添加完全限定域名 (FQDN)。 但是，对于在 Active Directory 注册的用户，此格式无效，该工具将生成的 UPN 导致以下错误消息进行 Kerberos 身份验证失败：**登录尝试失败。** 若要解决此问题，请手动修复该工具生成的客户端文件。  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>引用和共享类型  
  
|选项|描述|  
|------------|-----------------|  
|**/reference:\<文件路径 >**|引用指定程序集中的类型。 在生成客户端时，使用此选项来指定可能包含类型的程序集，这些类型表示所导入的元数据。<br /><br /> 缩写形式： `/r`|  
|**/excludeType:\<type>**|指定要从引用的协定类型中排除的完全限定或程序集限定类型名称。<br /><br /> 缩写形式： `/et`|  
  
## <a name="choosing-a-serializer"></a>选择序列化程序  
  
|选项|描述|  
|------------|-----------------|  
|**/serializer:Auto**|自动选择序列化程序。 此操作使用 `DataContract` 序列化程序。 如果此操作失败，则使用 `XmlSerializer`。<br /><br /> 缩写形式： `/ser:Auto`|  
|**/serializer:DataContractSerializer**|生成使用 `DataContract` 序列化程序进行序列化和反序列化的数据类型。<br /><br /> 缩写形式： `/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|生成使用 `XmlSerializer` 进行序列化和反序列化的数据类型。<br /><br /> 缩写形式： `/ser:XmlSerializer`|  
|**/importXmlTypes**|配置 `DataContract` 序列化程序，以便将非 `DataContract` 类型作为 `IXmlSerializable` 类型导入。<br /><br /> 缩写形式： `/ixt`|  
|**/dataContractOnly**|只为 `DataContract` 类型生成代码。 `ServiceContract` 会生成类型。<br /><br /> 应该仅为此选项指定本地元数据文件。<br /><br /> 缩写形式： `/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>为客户端选择语言  
  
|选项|描述|  
|------------|-----------------|  
|**/language:\<语言 >**|指定要用于代码生成的编程语言。 提供在 Machine.config 文件中注册的语言名称或从 <xref:System.CodeDom.Compiler.CodeDomProvider> 继承的类的完全限定名称。<br /><br /> 值：C#、cs、csharp、vb、vbs、visualbasic、vbscript、javascript、c++、mc、cpp<br /><br /> 默认设置：csharp<br /><br /> 缩写形式： `/l`<br /><br /> 有关详细信息，请参阅[CodeDomProvider 类](https://go.microsoft.com/fwlink/?LinkId=94778)。|  
  
## <a name="choosing-a-namespace-for-the-client"></a>为客户端选择命名空间  
  
|选项|描述|  
|------------|-----------------|  
|**/namespace:\<string,string>**|指定从 WSDL 或 XML 架构 `targetNamespace` 到公共语言运行库 (CLR) 命名空间的映射。 将通配符 (*) 用于 `targetNamespace` 将映射所有 `targetNamespaces`，而不显式映射到该 CLR 命名空间。<br /><br /> 若要确保消息协定名称不与操作名称相冲突，请用双冒号 (`::`) 限定类型引用，或者确保名称是唯一的。<br /><br /> 默认：派生自的架构文档的目标命名空间`DataContracts`。 默认命名空间用于所有其他生成的类型。<br /><br /> 缩写形式： `/n`|  
  
## <a name="choosing-a-data-binding"></a>选择数据绑定  
  
|选项|描述|  
|------------|-----------------|  
|**/enableDataBinding**|在所有 <xref:System.ComponentModel.INotifyPropertyChanged> 类型上实现 `DataContract` 接口以启用数据绑定。<br /><br /> 缩写形式： `/edb`|  
  
## <a name="generating-configuration"></a>生成配置  
  
|选项|描述|  
|------------|-----------------|  
|**/config:\<configFile>**|指定已生成的配置文件的文件名。<br /><br /> 默认设置：output.config|  
|**/mergeConfig**|将生成的配置合并到现有文件中，而不是覆盖现有文件。|  
|**/noConfig**|不生成配置文件。|  
  
## <a name="see-also"></a>请参阅

- [使用元数据](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [元数据体系结构概述](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
