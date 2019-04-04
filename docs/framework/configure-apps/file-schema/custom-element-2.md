---
title: NameValueSectionHandler 和 DictionarySectionHandler 的自定义元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 731e52958b89886c2bc069c4c181c0cc3928d487
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845704"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>NameValueSectionHandler 和 DictionarySectionHandler 的自定义元素

定义使用的自定义配置部分设置<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>类。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a>特性

None

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | 公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<添加 >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md)为<xref:System.Configuration.NameValueSectionHandler>和 <xref:System.Configuration.DictionarySectionHandler>  | 添加自定义应用程序设置。 |
| [**\<删除 >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md)为<xref:System.Configuration.NameValueSectionHandler>和 <xref:System.Configuration.DictionarySectionHandler> | 删除以前定义的设置。 |
| [**\<清除 >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md)为<xref:System.Configuration.NameValueSectionHandler>和 <xref:System.Configuration.DictionarySectionHandler> | 清除部分中的所有以前定义的设置。 |

## <a name="remarks"></a>备注

 **\<SectionName >** 元素是通过定义的自定义元素**\<部分 >** 标记中的 **\<configSections >** 元素。

下表显示了为每个配置节处理程序返回的对象 ConfigurationSettings.GetConfig 方法的类型：

| 配置节处理程序                        | 返回类型                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>示例

下面的示例演示如何声明使用的部分<xref:System.Configuration.DictionarySectionHandler>和<xref:System.Configuration.NameValueSectionHandler>类。

第一个自定义元素是 **\<dictionarySample >**，其中包含设置读取<xref:System.Configuration.DictionarySectionHandler>类`System.dll`程序集。 第二个自定义元素是 **\<mySection >**，其中包含设置读取<xref:System.Configuration.NameValueSectionHandler>类`System.dll`程序集。

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>配置文件

在应用程序配置文件中，计算机配置文件可以使用此元素 (*Machine.config*)，并*Web.config*不在应用程序目录级别上的文件。

## <a name="see-also"></a>请参阅

- [.NET Framework 的配置文件架构](~/docs/framework/configure-apps/file-schema/index.md)
