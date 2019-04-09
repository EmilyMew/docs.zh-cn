---
title: 使用 XmlSerializer 类
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
ms.openlocfilehash: 29ce9b165c3823d7d06008431294f67716ccf8e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105438"
---
# <a name="using-the-xmlserializer-class"></a>使用 XmlSerializer 类
Windows Communication Foundation (WCF) 可以使用两种不同的序列化技术将客户端和服务，名为序列化的进程之间进行传输的 XML 应用程序中的数据。  
  
## <a name="datacontractserializer-as-the-default"></a>DataContractSerializer 为默认序列化程序  
 默认情况下使用 WCF<xref:System.Runtime.Serialization.DataContractSerializer>类序列化的数据类型。 此序列化程序支持下列类型：  
  
-   基元类型（如：整数、字符串和字节数组）以及某些特殊类型（如 <xref:System.Xml.XmlElement> 和 <xref:System.DateTime>），这些特殊类型也被视为基元类型。  
  
-   数据协定类型（用 <xref:System.Runtime.Serialization.DataContractAttribute> 属性标记的类型）。  
  
-   用 <xref:System.SerializableAttribute> 属性标记的类型，包括实现 <xref:System.Runtime.Serialization.ISerializable> 接口的类型。  
  
-   实现 <xref:System.Xml.Serialization.IXmlSerializable> 接口的类型。  
  
-   许多常见集合类型，包括许多泛型集合类型。  
  
 许多 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 类型属于后两种类别，因此可序列化。 可序列化类型的数组也可序列化。 有关完整列表，请参阅[Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>（与数据一起使用的协定类型) 是编写新的 WCF 服务的建议的方法。 有关详细信息，请参阅[Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)。  
  
## <a name="when-to-use-the-xmlserializer-class"></a>使用 XmlSerializer 类的时机  
 WCF 还支持<xref:System.Xml.Serialization.XmlSerializer>类。 <xref:System.Xml.Serialization.XmlSerializer>类不是唯一的 WCF。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服务同样使用该类作为序列化引擎。 <xref:System.Xml.Serialization.XmlSerializer> 类支持的类型少于 <xref:System.Runtime.Serialization.DataContractSerializer> 类支持的类型，但它允许对生成的 XML 进行更多的控制，并且支持更多的 XML 架构定义语言 (XSD) 标准。 它也不要求针对可序列化类型的任何声明性属性。 有关详细信息，请参阅中的 XML 序列化主题[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]文档。 <xref:System.Xml.Serialization.XmlSerializer> 类并不支持数据协定类型。  
  
 当使用 Svcutil.exe 或**添加服务引用**自动为您选择在 Visual Studio 中生成客户端代码，对于第三方服务，或访问第三方架构，相应的序列化程序的功能。 如果架构与 <xref:System.Runtime.Serialization.DataContractSerializer> 不兼容，则选择 <xref:System.Xml.Serialization.XmlSerializer>。  
  
## <a name="manually-switching-to-the-xmlserializer"></a>手动切换到 XmlSerializer  
 有时候，您也许必须手动切换到 <xref:System.Xml.Serialization.XmlSerializer>。 例如，在以下情况下可能需要这样做：  
  
-   当迁移应用程序从[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]wcf Web 服务，你可能想要重用现有的、 <xref:System.Xml.Serialization.XmlSerializer>-兼容的类型，而不是创建新的数据协定类型。  
  
-   当对出现在消息中的 XML 的精确控制很重要，而 Web 服务描述语言 (WSDL) 文档不可用时，例如，在使用必须遵循某个已标准化且已发布的架构（与 DataContractSerializer 不兼容）的类型来创建服务时。  
  
-   创建遵循旧式 SOAP 编码标准的服务时。  
  
 在这些情况和其他情况下，你可以通过将 <xref:System.Xml.Serialization.XmlSerializer> 属性应用于你的服务来手动切换到 `XmlSerializerFormatAttribute` 类，如以下代码所示。  
  
 [!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
 [!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]  
  
## <a name="security-considerations"></a>安全注意事项  
  
> [!NOTE]
>  切换序列化引擎时需要小心，这一点非常重要。 根据所使用的序列化程序，相同的类型可以序列化为不同的 XML。 如果意外使用了错误的序列化程序，则可能会公开类型中您不希望公开的信息。  
  
 例如，在序列化数据协定类型时，<xref:System.Runtime.Serialization.DataContractSerializer> 类只序列化用 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性标记的成员。 <xref:System.Xml.Serialization.XmlSerializer> 类序列化任何公共成员。 请看以下代码中的类型。  
  
 [!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
 [!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]  
  
 如果在选择了 <xref:System.Xml.Serialization.XmlSerializer> 类的服务协定中不慎使用了该类型，则将序列化 `creditCardNumber` 成员，这可能并不是想要的结果。  
  
 即使 <xref:System.Runtime.Serialization.DataContractSerializer> 类为默认值，您也可以通过将 <xref:System.ServiceModel.DataContractFormatAttribute> 属性应用于服务协定类型来为您的服务显式选择此类（虽然从不要求进行此项操作）。  
  
 用于服务的序列化程序是协定的不可分割的一部分，你无法通过选择不同的绑定或更改其他配置设置来对其进行更改。  
  
 此外，在使用 <xref:System.Xml.Serialization.XmlSerializer> 类时还需注意以下重要安全事项。 首先，我们强烈建议，任何 WCF 应用程序的使用<xref:System.Xml.Serialization.XmlSerializer>类不会泄露的密钥进行签名。 在执行手动切换到 <xref:System.Xml.Serialization.XmlSerializer> 和执行自动切换（通过 Svcutil.exe、添加服务引用或类似工具）时都适合采用此建议。 这是因为<xref:System.Xml.Serialization.XmlSerializer>序列化引擎支持的加载*预生成序列化程序集*，只要它们使用与应用程序相同的密钥进行签名。 如果某恶意程序集的名称与放置在应用程序文件夹或全局程序集缓存中的预生成序列化程序集的预期名称相匹配，则未签名的应用程序对于此类恶意程序集的攻击完全没有防御能力。 当然，攻击者必须首先获取对这两个位置中某个位置的写权限才能尝试进行攻击。  
  
 您使用 <xref:System.Xml.Serialization.XmlSerializer> 时存在的另一个威胁与系统临时文件夹的写权限有关。 <xref:System.Xml.Serialization.XmlSerializer>序列化引擎创建，并使用临时*序列化程序集*此文件夹中。 你应该注意，任何对临时文件夹具有写权限的进程都可能用恶意代码覆盖这些序列化程序集。  
  
## <a name="rules-for-xmlserializer-support"></a>XmlSerializer 支持的规则  
 您不能直接将与兼容 <xref:System.Xml.Serialization.XmlSerializer> 的属性应用于协定操作参数或返回值。 但是，可将这些属性应用于类型化消息（消息协定正文部分），如以下代码所示。  
  
 [!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
 [!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]  
  
 当应用于类型化消息成员时，这些属性 (Attribute) 将覆盖与类型化消息属性 (Attribute) 相冲突的属性 (Property)。 例如，在下列代码中，`ElementName` 覆盖 `Name`。  
  
 [!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
 [!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]  
  
 使用 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 时不支持 <xref:System.Xml.Serialization.XmlSerializer> 属性。  
  
> [!NOTE]
>  在这种情况下，<xref:System.Xml.Serialization.XmlSerializer>引发以下异常，在 WCF 之前发布："在架构的顶级声明的元素不能具有`maxOccurs`> 1。 使用 `XmlArray` 或 `XmlArrayItem` 而不是 `XmlElementAttribute`，或使用换行的参数样式为“more”提供包装元素。”  
>   
>  如果您接收到此异常，请调查是否属于这种情况。  
  
 WCF 不支持<xref:System.Xml.Serialization.SoapIncludeAttribute>并<xref:System.Xml.Serialization.XmlIncludeAttribute>属性在消息协定和操作协定; 使用<xref:System.Runtime.Serialization.KnownTypeAttribute>特性。  
  
## <a name="types-that-implement-the-ixmlserializable-interface"></a>用于实现 IXmlSerializable 接口的类型  
 `IXmlSerializable` 完全支持实现 `DataContractSerializer` 接口的类型。 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 属性应始终应用于这些类型以控制它们的架构。  
  
> [!WARNING]
>  如果您要序列化多态类型，则必须将 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 应用于该类型以确保序列化正确的类型。  
  
 实现 `IXmlSerializable` 的类型有以下三种：表示任意内容的类型、表示单一元素的类型和旧的 <xref:System.Data.DataSet> 类型。  
  
-   内容类型使用由 `XmlSchemaProviderAttribute` 属性指定的架构提供程序方法。 该方法不返回 `null`，并且特性上的 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> 属性将保留为它的默认值 `false`。 这是 `IXmlSerializable` 类型的最常见的用法。  
  
-   当 `IXmlSerializable` 类型必须控制其根元素名称时，使用元素类型。 若要将某类型标记为元素类型，请将 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> 特性上的 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 属性设置为 `true`，或者从架构提供程序方法返回 `null`。 对于元素类型，具有架构提供程序方法是可选的 – 您可以在 `null` 中指定 `XmlSchemaProviderAttribute` 而不指定方法名称。 但是，如果 `IsAny` 为 `true`，并且已指定了架构提供程序方法，则该方法必须返回 `null`。  
  
-   旧 <xref:System.Data.DataSet> 类型为没有使用 `IXmlSerializable` 特性标记的 `XmlSchemaProviderAttribute` 类型。 相反，它们依赖于架构生成的 <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> 方法。 此模式用于 `DataSet` 类型，其类型化数据集在 .NET Framework 的早期版本中派生了一个类，但现在它已过时，并且只有旧版本才支持它。 不要依赖于此模式，并始终将 `XmlSchemaProviderAttribute` 应用于 `IXmlSerializable` 类型。  
  
### <a name="ixmlserializable-content-types"></a>IXmlSerializable 内容类型  
 如果序列化某类型的数据成员，而该类型实现 `IXmlSerializable` 且是以前定义的内容类型，则序列化程序编写该数据成员的包装元素，并将控制权传递给 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 方法。 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 实现可以编写任何 XML，其中包括将特性添加到包装元素。 `WriteXml` 完成后，序列化程序将关闭该元素。  
  
 如果反序列化某类型的数据成员，而该类型实现 `IXmlSerializable` 且是以前定义的内容类型，则反序列化程序将 XML 读取器放在该数据成员的包装元素上，并将控制权传递给 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 方法。 该方法必须读取整个元素，包括起始和结束标记。 请确保您的 `ReadXml` 代码可处理元素为空的情况。 此外，您的 `ReadXml` 实现也不应该依赖于以特殊方式进行命名的包装元素。 序列化程序所选的名称可以不同。  
  
 允许以多元方式分配 `IXmlSerializable` 内容类型，例如，分配给 <xref:System.Object> 类型的数据成员。 还允许类型实例为 null。 最后，可以在启用对象图保留的情况下使用 `IXmlSerializable` 类型，以及和 <xref:System.Runtime.Serialization.NetDataContractSerializer> 一起使用。 所有这些功能需要 WCF 序列化程序将某些属性附加到包装元素 ("nil"和"类型"XML 架构实例命名空间和"Id"、"Ref"、"类型"和"Assembly"中特定于 WCF 的命名空间中)。  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>实现 ReadXml 时要忽略的属性  
 在将控制权传递给 `ReadXml` 代码之前，反序列化程序将检查 XML 元素、检测这些特殊的 XML 属性，以及对它们进行操作。 例如，如果“nil”为 `true`，则将反序列化一个 Null 值，并且不调用 `ReadXml`。 如果检测到多态性，则将反序列化该元素的内容，就好像该元素为其他类型一样。 调用以多元方式分配的类型的 `ReadXml` 实现。 在任何情况下，`ReadXml` 实现都应忽略这些特殊属性，因为它们均由反序列化程序处理。  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>IXmlSerializable 内容类型的架构注意事项  
 当导出架构和 `IXmlSerializable` 内容类型时，将调用架构提供程序方法。 并将 <xref:System.Xml.Schema.XmlSchemaSet> 传递给架构提供程序方法。 该方法可以将任何有效架构添加到架构集中。 该架构集将包含发生架构导出时已知的架构。 当架构提供程序方法必须将某项添加到架构集时，它必须确定该集中是否已存在具有相应命名空间的 <xref:System.Xml.Schema.XmlSchema>。 如果已存在，则架构提供程序方法必须将新项添加到现有 `XmlSchema` 中。 否则，它必须创建一个新的 `XmlSchema` 实例。 如果使用的是 `IXmlSerializable` 类型数组，这是非常重要的。 例如，如果您有一个 `IXmlSerializable` 类型，且已作为命名空间“B”中的类型“A”导出，则在调用架构提供程序方法时，架构集可能已包含保存“ArrayOfA”类型的“B”架构。  
  
 除了将类型添加到 <xref:System.Xml.Schema.XmlSchemaSet>，内容类型的架构提供程序方法必须返回非空值。 它可能返回 <xref:System.Xml.XmlQualifiedName>，指定用于给定 `IXmlSerializable` 类型的架构类型名称。 此限定名称也将用作数据协定名称和该类型的命名空间。 返回架构提供程序方法时允许立即返回架构集中不存在的类型。 但是，导出所有相关类型（调用 <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> 方法中有关 <xref:System.Runtime.Serialization.XsdDataContractExporter> 的所有相关类型并访问 <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> 属性）时，该类型应该存在于架构集中。 在进行所有相关的 `Schemas` 调用之前访问 `Export` 属性可能会导致 <xref:System.Xml.Schema.XmlSchemaException>。 有关导出过程的详细信息，请参阅[从类导出架构](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)。  
  
 架构提供程序方法也可以返回要使用的 <xref:System.Xml.Schema.XmlSchemaType>。 该类型可能是匿名的，也可能不是。 如果它是匿名的，则每次将 `IXmlSerializable` 类型用作数据成员时，`IXmlSerializable` 类型的架构都将作为匿名类型导出。 `IXmlSerializable` 类型仍具有数据协定名称和命名空间。 (这确定中所述[Data Contract Names](../../../../docs/framework/wcf/feature-details/data-contract-names.md)只不过<xref:System.Runtime.Serialization.DataContractAttribute>属性不能用于自定义的名称。)如果它不是匿名的，则它必须是 `XmlSchemaSet` 中的一种类型。 这种情况相当于返回该类型的 `XmlQualifiedName`。  
  
 另外，还将导出该类型的全局元素声明。 如果该类型没有应用于它的 <xref:System.Xml.Serialization.XmlRootAttribute> 特性，则该元素具有与数据协定相同的名称和命名空间，且其“nillable”属性为 `true`。 唯一的例外是架构命名空间 (`http://www.w3.org/2001/XMLSchema`) – 因为禁止将新元素添加到架构命名空间的相应的全局元素类型的数据协定是此命名空间中，如果是空白命名空间中。 如果该类型具有应用于它的 `XmlRootAttribute` 属性 (Attribute)，则将使用以下属性 (Property) 导出全局元素声明：<xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>、<xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> 和 <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A>。 应用了 `XmlRootAttribute` 的默认值是数据协定名称、空命名空间和为 `true` 的“nillable”。  
  
 同样的全局元素声明规则也适用于旧数据集类型。 请注意，`XmlRootAttribute` 无法重写通过自定义代码添加的全局元素声明，无论是使用构架提供程序方法添加到 `XmlSchemaSet` 中的，还是通过旧数据集类型的 `GetSchema` 添加的。  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable 元素类型  
 `IXmlSerializable` 元素类型`IsAny`属性设置为`true`或使其架构提供程序方法返回`null`。  
  
 序列化和反序列化元素类型与序列化和反序列化内容类型极其相似。 但是，也有一些重要的区别：  
  
-   `WriteXml` 实现应只写入一个元素（当然，该元素可包含多个子元素）。 它不应是此单个元素、多个同级元素或混合内容以外的写属性。 该元素可能为空。  
  
-   `ReadXml` 实现不应读取包装元素。 它应读取 `WriteXml` 生成的那一个元素。  
  
-   定期序列化元素类型时（例如，作为数据协定中的数据成员），序列化程序将在调用 `WriteXml` 之前输出包装元素，如同处理内容类型一样。 然而，在顶层序列化元素类型时，序列化程序通常根本不输出 `WriteXml` 写入的元素周围的包装元素，除非在 `DataContractSerializer` 或 `NetDataContractSerializer` 构造函数中构造序列化程序时显式指定了根名称和命名空间。 有关详细信息，请参阅[序列化和反序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)。  
  
-   如果在构造期间没有指定根名称和命名空间的情况下在顶层序列化元素类型，则 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> 和 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> 实质上不执行任何操作，且 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> 将调用 `WriteXml`。 在此模式下，要序列化的对象不能为 `null`，且不能以多态形式进行分配。 另外，不能启用对象图保留，也不能使用 `NetDataContractSerializer`。  
  
-   如果在构造时没有指定根名称和命名空间的情况下在顶级反序列化某一元素类型，则在找到任何元素的开头时，<xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> 将返回 `true`。 <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> 与`verifyObjectName`参数设置为`true`的行为方式与`IsStartObject`之前实际读取该对象。 `ReadObject` 然后将控制权传递给`ReadXml`方法。  
  
 如上节所述，元素类型的导出架构与 `XmlElement` 类型的导出架构相同，只是架构提供程序方法可以像处理内容类型那样将任何其他架构添加到 <xref:System.Xml.Schema.XmlSchemaSet> 中。 不允许使用元素类型的 `XmlRootAttribute` 属性，也从不为这些类型发出全局元素声明。  
  
### <a name="differences-from-the-xmlserializer"></a>与 XmlSerializer 的区别  
 `IXmlSerializable` 接口以及 `XmlSchemaProviderAttribute` 和 `XmlRootAttribute` 属性也都可以由 <xref:System.Xml.Serialization.XmlSerializer> 理解。 但是，在数据协定模型中处理它们的方法有一些不同。 下表汇总了重要区别：  
  
-   架构提供程序方法必须是公共方法才能在 `XmlSerializer` 中使用，但是它不必是公共方法即可在数据协定模型中使用。  
  
-   如果在数据协定模型中 `IsAny` 为 `true` 但是不具有 `XmlSerializer`，则调用架构提供程序方法。  
  
-   如果内容或旧数据集类型中没有 `XmlRootAttribute` 属性，则 `XmlSerializer` 将在空白命名空间中导出全局元素声明。 如前面所述，在数据协定模型中，使用的命名空间通常是数据协定命名空间。  
  
 创建与这两种序列化技术一起使用的类型时，请注意这些区别。  
  
### <a name="importing-ixmlserializable-schema"></a>导入 IXmlSerializable 架构  
 导入从 `IXmlSerializable` 类型生成的架构时，有以下几种可能：  
  
-   生成的架构可能是有效的数据协定架构中所述[数据协定架构参考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。 在此情况下，架构可以正常导入，并且将生成常规数据协定类型。  
  
-   生成的架构可能不是有效的数据协定架构。 例如，架构提供程序方法生成的架构可能包含在数据协定模型中不受支持的 XML 特性。 在此情况下，您可以将架构作为 `IXmlSerializable` 类型导入。 默认情况下未在此导入模式，但可以轻松地使用来启用 – 例如，`/importXmlTypes`到命令行开关[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 详细介绍[导入架构以生成类](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)。 请注意，您必须直接处理您的类型实例的 XML。 您也可以考虑使用其他支持各种架构的不同序列化技术 – 请参见有关使用 `XmlSerializer` 的主题。  
  
-   您可能希望重新使用代理中的现有 `IXmlSerializable` 类型，而不生成新的类型。 在此情况下，“导入架构以生成类型”主题中介绍的引用类型功能可用于指示要重新使用的类型。 这对应于在 svcutil.exe 上使用 `/reference` 开关，以指定包含要重新使用的类型的程序集。  
  
### <a name="xmlserializer-legacy-behavior"></a>XmlSerializer Legacy Behavior  
 在 .NET Framework 4.0 和更早版本中，XmlSerializer 通过将 C# 代码写入某一文件，生成临时序列化程序集。 然后将该文件编译为一个程序集。  这种行为会产生不想要的结果，例如序列化程序的启动时间延长。 在 .NET Framework 4.5 中，已对此行为进行了更改，无需使用该编译器即可生成程序集。 一些开发人员可能希望看到生成的 C# 代码。 您可以通过以下配置指定为使用这一旧行为：  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer tempFilesLocation='e:\temp\XmlSerializerBug' useLegacySerializerGeneration="true" />  
  </system.xml.serialization>  
  <system.diagnostics>  
    <switches>  
      <add name="XmlSerialization.Compilation" value="1" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
 如果遇到兼容性问题，如`XmlSerializer`无法序列化的非公共新重写的派生的类，您可以切换回`XMLSerializer`旧行为，通过使用以下配置：  
  
```xml  
<configuration>  
<appSettings>   
<add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />  
               </appSettings>  
</configuration>  
```  
  
 作为上述配置的替代方法，可以运行.NET Framework 4.5 或更高版本的计算机上使用以下配置：  
  
```xml  
<configuration>  
<system.xml.serialization>  
<xmlSerializer useLegacySerializerGeneration="true"/>  
</system.xml.serialization>  
</configuration>  
```  
  
> [!NOTE]
>  `<xmlSerializer useLegacySerializerGeneration="true"/>`交换机仅适用于运行.NET Framework 4.5 或更高版本的计算机。 上述`appSettings`方法适用于所有.NET Framework 版本上。  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.DataContractFormatAttribute>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.MessageHeaderArrayAttribute>
- [在服务协定中指定数据传输](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [使用数据协定](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [如何：使用 XmlSerializer 改善 WCF 客户端应用程序的启动时间](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
