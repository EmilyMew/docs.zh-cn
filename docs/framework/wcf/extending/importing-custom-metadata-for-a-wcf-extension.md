---
title: 导入 WCF 扩展的自定义元数据
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: 021790a256448d9c81e7a53a2845edf839ff3534
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090064"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>导入 WCF 扩展的自定义元数据
在 Windows Communication Foundation (WCF) 的元数据导入是从其元数据生成的服务或其各个组成部分的抽象表示形式的过程。 例如，可以导入 WCF<xref:System.ServiceModel.Description.ServiceEndpoint>情况下，<xref:System.ServiceModel.Channels.Binding>实例或<xref:System.ServiceModel.Description.ContractDescription>实例从 WSDL 文档的服务。 若要导入 WCF 服务元数据，请使用的实现<xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType>抽象类。 派生的类型<xref:System.ServiceModel.Description.MetadataImporter>类实现的支持，为利用 WS 策略的导入元数据格式导入 WCF 中的逻辑。  
  
 自定义元数据包含系统提供的元数据导入程序无法导入的 XML 元素。 通常情况下，这包括自定义 WSDL 扩展和自定义策略断言。  
  
 本节描述如何导入自定义 WSDL 扩展和策略断言。 本节的重点并非导入过程本身。 有关如何使用导出和导入元数据，而不管元数据是自定义的还是系统支持的类型的详细信息，请参阅[导出和导入元数据](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)。  
  
## <a name="overview"></a>概述  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>类型是实现<xref:System.ServiceModel.Description.MetadataImporter>抽象 WCF 中包含的类。 <xref:System.ServiceModel.Description.WsdlImporter> 类型可以导入含有附加策略（这些策略捆绑在 <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> 对象中）的 WSDL 元数据。 默认导入程序无法识别的策略断言和 WSDL 扩展会被传送给任何已注册的自定义策略和 WSDL 导入程序，以便进行导入。 通常，导入程序的实现应该能够支持用户定义的绑定元素或修改已导入的协定。  
  
 本节介绍以下内容：  
  
1.  如何实现和使用 <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> 接口，该接口在生成说明和代码之前向自定义导入程序公开 WSDL 数据。 可以使用此接口检查或修改使用给定元数据集执行的说明类型和代码编译。  
  
2.  如何实现和使用 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> 接口，该接口在生成说明对象之前向导入程序公开策略断言。 可以使用此接口检查或修改基于所下载策略的绑定或协定。  
  
 有关导出自定义 WSDL 和策略断言的详细信息，请参阅[导出 WCF 扩展的自定义元数据](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)。  
  
## <a name="importing-custom-wsdl-extensions"></a>导入自定义 WSDL 扩展  
 若要添加对导入 WSDL 扩展的支持，请实现 <xref:System.ServiceModel.Description.IWsdlImportExtension> 接口，然后将实现添加到 <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> 属性。 <xref:System.ServiceModel.Description.WsdlImporter> 还可以加载应用程序配置文件中注册的 <xref:System.ServiceModel.Description.IWsdlImportExtension> 接口的实现。 请注意，默认情况下会注册许多 WSDL 导入程序，并且已注册的 WSDL 导入程序的顺序很重要。  
  
 当 <xref:System.ServiceModel.Description.WsdlImporter> 加载并使用自定义 WSDL 导入程序时，将首先调用 <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> 方法以便在导入过程开始之前修改元数据。 接下来将导入协定，并随后调用 <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> 方法以便对从元数据导入的协定进行修改。 最后，调用<xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> 方法以便对导入的终结点进行修改。  
  
 有关详细信息，请参阅[如何：导入自定义 WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)。  
  
### <a name="importing-custom-policy-assertions"></a>导入自定义策略断言  
 <xref:System.ServiceModel.Description.WsdlImporter>类型和[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)自动处理不同的策略表达式附加到 WSDL 文档中的策略断言类型。 这些工具可以收集、规范化和合并附加到 WSDL 绑定和 WSDL 端口的策略表达式。  
  
 若要添加对导入自定义策略断言的支持，请实现 <xref:System.ServiceModel.Description.IPolicyImportExtension> 接口，然后将实现添加到 <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> 属性。 <xref:System.ServiceModel.Description.MetadataImporter> 还可以加载应用程序配置文件中注册的 <xref:System.ServiceModel.Description.IPolicyImportExtension> 接口的实现。 请注意，默认情况下会注册许多策略导入程序，并且已注册的策略导入程序的顺序很重要。  
  
 元数据系统会对所有已注册的策略导入扩展反复调用 <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> 方法，以获取附加到消息、操作和终结点策略主题上的策略替代项的每个组合。 在导入 WSDL 端口时，将首先合并附加到端口以及附加到相应的 WSDL 绑定的策略，然后再调入策略导入扩展。 策略替代项是以 <xref:System.ServiceModel.Description.PolicyConversionContext> 对象的形式通过 <xref:System.ServiceModel.Description.PolicyAssertionCollection> 提供的。 每个 <xref:System.ServiceModel.Description.PolicyAssertionCollection> 都是由 <xref:System.Xml.XmlElement> 对象表示的策略断言的集合。  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> 对象上的 <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> 和 <xref:System.ServiceModel.Description.PolicyConversionContext> 属性公开了从 WSDL 导入的 <xref:System.ServiceModel.Description.ContractDescription> 和 <xref:System.ServiceModel.Channels.BindingElement> 对象。 策略导入扩展通过以下方式处理策略断言：查找特定策略断言类型的实例、对 <xref:System.ServiceModel.Description.ContractDescription> 或 <xref:System.ServiceModel.Channels.BindingElement> 对象进行相应的更改，然后从相应的 <xref:System.ServiceModel.Description.PolicyAssertionCollection> 实例中删除策略断言。  
  
 由于不会对 `wsp:Optional` 属性和嵌套的策略表达式进行规范化，因此策略导入扩展必须处理这些策略构造。 另外，具有相同的 <xref:System.ServiceModel.Description.ContractDescription> 和 <xref:System.ServiceModel.Channels.BindingElement> 对象的策略导入扩展可能会被调用多次，因此策略导入扩展应该足够可靠以便适应这一行为。  
  
> [!IMPORTANT]
>  可能将无效或不正确的元数据传递给导入程序。 请确保自定义导入程序对所有形式的 XML 都能保持可靠性。  
  
## <a name="see-also"></a>请参阅

- [如何：导入自定义 WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
- [如何：导人自定义策略断言](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
- [如何：编写 ServiceContractGenerator 的扩展](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
