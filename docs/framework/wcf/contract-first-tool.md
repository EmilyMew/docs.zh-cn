---
title: 协定优先工具
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: ad0566eaff08d27e8368f091388adda7376a37ef
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819614"
---
# <a name="contract-first-tool"></a>协定优先工具
服务协定往往需要从现有的服务创建。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，可以使用协定优先工具从现有服务自动创建数据协定类。 要使用协定优先工具，必须本地下载 XML 架构定义 (XSD) 文件；该工具无法通过 HTTP 导入远程数据协定。

 协定优先工具作为生成任务集成到 Visual Studio 2012。 由生成任务所生成的代码文件在每次生成项目时创建，以使项目可以轻松地采用基础服务协定中的更改。

 协定优先工具可以导入的架构类型包括：

```xml
<xsd:complexType>
<xsd:simpleType>
```

 如果它们是基元（如 `Int16` 或 `String`），将不会生成简单类型；如果它们的类型为 `Collection`，将不会生成复杂类型。 如果它们是另一 `xsd:complexType` 的组成部分，则也不会生成类型。 在所有这些情况下，这些类型将会被引用到项目中的现有类型。

## <a name="adding-a-data-contract-to-a-project"></a>向项目中添加数据协定
 使用协定优先工具之前，服务协定 (XSD) 必须添加到项目中。 出于本概述的需要，以下协定将用于阐述协定优先函数。 此服务定义是 Bing 的搜索 API 所使用的服务协定的一个小子集。

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema id="ServiceSchema"
    targetNamespace="http://tempuri.org/ServiceSchema.xsd"
    elementFormDefault="qualified"
    xmlns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:mstns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
>
  <xs:complexType name="SearchRequest">
    <xs:sequence>
      <xs:element minOccurs="0" maxOccurs="1" name="Version" type="xs:string" default="2.2" />
      <xs:element minOccurs="0" maxOccurs="1" name="Market" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="UILanguage" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="Query" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="AppId" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="Latitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Longitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Radius" type="xs:double" />
    </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="WebSearchOption">
    <xs:restriction base="xs:string">
      <xs:enumeration value="DisableHostCollapsing" />
      <xs:enumeration value="DisableQueryAlterations" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

 若要向项目添加上述服务协定，请右键单击该项目并选择**添加新...**. 从“模板”对话框的 WCF 窗格中选择架构定义，然后将新文件命名为 SampleContract.xsd。 复制上面的代码并粘贴到新文件的代码视图中。

## <a name="configuring-contract-first-options"></a>配置协定优先选项
 协定优先选项可以配置 WCF 项目中的属性菜单中。 若要启用协定优先开发，请选择**XSD 作为类型定义语言**项目属性窗口的 WCF 页中的复选框。

 ![协定优先开发启用 WCF 选项的屏幕截图。](./media/contract-first-tool/contract-first-options.png)

 要配置高级属性，请单击“高级”按钮。

 ![高级的协定代码生成设置对话框。](./media/contract-first-tool/advanced-contract-settings.png)

 可以从协定中配置下列高级设置用于代码生成。 只能为项目中的所有文件配置设置；目前不能为单独的文件配置设置。

-   **序列化程序模式**:此设置确定哪个序列化程序用于读取服务协定文件。 时**XML 序列化程序**已选中**集合类型**并**重用类型**选项处于禁用状态。 这些选项仅适用于**数据协定序列化程序**。

-   **重新使用的类型**:此设置指定哪些库用于类型重用。 此设置才适用**序列化程序模式**设置为**数据协定序列化程序**。

-   **集合类型**:此设置指定要用作集合数据类型的完全限定或程序集限定类型。 此设置才适用**序列化程序模式**设置为**数据协定序列化程序**。

-   **字典类型**:此设置指定要用于字典数据类型的完全限定或程序集限定类型。

-   **EnableDataBinding**:此设置指定是否实现<xref:System.ComponentModel.INotifyPropertyChanged>上所有数据类型实现数据绑定接口。

-   **ExcludedTypes**： 此设置指定的完全限定或程序集限定类型引用的程序集从排除列表。 此设置才适用**序列化程序模式**设置为**数据协定序列化程序**。

-   **GenerateInternalTypes**:此设置指定是否生成标记为内部的类。 此设置才适用**序列化程序模式**设置为**数据协定序列化程序**。

-   **GenerateSerializableTypes**:此设置指定是否生成与类<xref:System.SerializableAttribute>属性。 此设置才适用**序列化程序模式**设置为**数据协定序列化程序**。

-   **ImportXMLTypes**:此设置指定是否将配置数据协定序列化程序，以应用<xref:System.SerializableAttribute>属性为类，而<xref:System.Runtime.Serialization.DataContractAttribute>属性。  此设置才适用**序列化程序模式**设置为**数据协定序列化程序**。

-   **SupportFx35TypedDataSets**:此设置指定是否向为.NET Framework 3.5 创建的类型化数据集提供其他功能。 当**序列化程序模式**设置为**XML 序列化程序**，则<xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35>扩展将添加到 XML 架构导入程序，此值设置为 True 时。 当**序列化程序模式**设置为**数据协定序列化程序**，类型<xref:System.DateTimeOffset>时此值设置为 False，将排除从引用，以便<xref:System.DateTimeOffset>始终生成对于较早的 framework 版本。

-   **InputXsdFiles**:此设置指定输入文件的列表。 每个文件都必须包含有效的 XML 架构。

-   **语言**:此设置指定生成的协定代码的语言。 该设置必须为 <xref:System.CodeDom.Compiler.CodeDomProvider> 所识别。

-   **NamespaceMappings**:此设置指定从 XSD 目标命名空间到 CLR 命名空间的映射。 每个映射应使用以下格式：

    ```xml
    "<Schema Namespace>, <CLR Namespace>"
    ```

     XML 序列化程序只接受以下格式的一个映射：

    ```xml
    "*, <CLR Namespace>"
    ```

-   **OutputDirectory**:此设置指定将生成的代码文件的目录。

 这些设置将用于在生成项目时从服务协定文件中生成服务协定类型。

## <a name="using-contract-first-development"></a>使用协定优先开发
 向项目添加服务协定并确认生成设置中，通过按生成项目后**F6**。 然后，服务协定中定义的类型将可用于项目中。

 若要使用在服务协定中定义的类型，请在当前命名空间下添加对 `ContractTypes` 的引用：

```csharp
using MyProjectNamespace.ContractTypes;
```

 服务协定中定义的类型然后，将在项目中，可解析，如下所示：

 ![SearchRequest 类键入前几个字母后显示在 IntelliSense 中。](./media/contract-first-tool/service-contract-types.png)

 在 GeneratedXSDTypes.cs 文件中创建由工具生成的类型。 中创建的文件\<项目目录 > /obj/\<生成配置 > /XSDGeneratedCode/ 目录默认情况下。 本主题开头的示例架构转换为如下所示：

```csharp
//------------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by a tool.
//     Runtime Version:4.0.30319.17330
//
//     Changes to this file may cause incorrect behavior and will be lost if
//     the code is regenerated.
// </auto-generated>
//------------------------------------------------------------------------------

namespace TestXSD3.ContractTypes
{
    using System.Xml.Serialization;

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Diagnostics.DebuggerStepThroughAttribute()]
    [System.ComponentModel.DesignerCategoryAttribute("code")]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=true)]
    public partial class SearchRequest
    {

        private string versionField;

        private string marketField;

        private string uILanguageField;

        private string queryField;

        private string appIdField;

        private double latitudeField;

        private bool latitudeFieldSpecified;

        private double longitudeField;

        private bool longitudeFieldSpecified;

        private double radiusField;

        private bool radiusFieldSpecified;

        public SearchRequest()
        {
            this.versionField = "2.2";
        }

        /// <remarks/>
        [System.ComponentModel.DefaultValueAttribute("2.2")]
        public string Version
        {
            get
            {
                return this.versionField;
            }
            set
            {
                this.versionField = value;
            }
        }

        /// <remarks/>
        public string Market
        {
            get
            {
                return this.marketField;
            }
            set
            {
                this.marketField = value;
            }
        }

        /// <remarks/>
        public string UILanguage
        {
            get
            {
                return this.uILanguageField;
            }
            set
            {
                this.uILanguageField = value;
            }
        }

        /// <remarks/>
        public string Query
        {
            get
            {
                return this.queryField;
            }
            set
            {
                this.queryField = value;
            }
        }

        /// <remarks/>
        public string AppId
        {
            get
            {
                return this.appIdField;
            }
            set
            {
                this.appIdField = value;
            }
        }

        /// <remarks/>
        public double Latitude
        {
            get
            {
                return this.latitudeField;
            }
            set
            {
                this.latitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LatitudeSpecified
        {
            get
            {
                return this.latitudeFieldSpecified;
            }
            set
            {
                this.latitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Longitude
        {
            get
            {
                return this.longitudeField;
            }
            set
            {
                this.longitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LongitudeSpecified
        {
            get
            {
                return this.longitudeFieldSpecified;
            }
            set
            {
                this.longitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Radius
        {
            get
            {
                return this.radiusField;
            }
            set
            {
                this.radiusField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool RadiusSpecified
        {
            get
            {
                return this.radiusFieldSpecified;
            }
            set
            {
                this.radiusFieldSpecified = value;
            }
        }
    }

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=false)]
    public enum WebSearchOption
    {

        /// <remarks/>
        DisableHostCollapsing,

        /// <remarks/>
        DisableQueryAlterations,
    }
}
```

## <a name="errors-and-warnings"></a>错误和警告
 分析 XSD 架构时遇到的错误和警告将显示为生成错误和警告。

## <a name="interface-inheritance"></a>接口继承
 在协定优先开发中无法使用接口继承；这与接口在其他操作中的行为方式一致。 为了使用继承基接口的接口，应使用两个单独的终结点。 第一个终结点使用继承的协定，第二个终结点实现基接口。
