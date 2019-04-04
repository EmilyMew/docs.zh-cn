---
title: Singletagsectionhandler 的自定义元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
ms.openlocfilehash: bfc2a916e37ac27d45746eb268912b3752f4d80f
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464432"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Singletagsectionhandler 的自定义元素

在定义的自定义配置节中定义设置\<部分 > 元素，并使用<xref:System.Configuration.SingleTagSectionHandler>类。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;*\<sectionName>*

## <a name="syntax"></a>语法

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>特性

属性和属性值是用户定义的。

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | 公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>备注

 **\<SectionName >** 元素是通过定义的自定义元素[ **\<部分 >** ](~/docs/framework/configure-apps/file-schema/section-element.md)标记中的[ **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)元素。 配置系统返回<xref:System.Collections.IDictionary>对象在调用时<xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>。

## <a name="example"></a>示例

下面的示例声明一个名为自定义元素 **\<sampleSection >** ，其中包含通过读取设置<xref:System.Configuration.SingleTagSectionHandler>类：

```xml
<configuration>
  <configSections>
    <section name="sampleSection" 
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>配置文件

在应用程序配置文件中，计算机配置文件可以使用此元素 (*Machine.config*)，并*Web.config*不在应用程序目录级别上的文件。

## <a name="see-also"></a>请参阅

- [.NET Framework 的配置文件架构](~/docs/framework/configure-apps/file-schema/index.md)
