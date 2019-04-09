---
title: <system.codedom> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 0f47255bb4073007a847e4a8b85ccfd34100582b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101609"
---
# <a name="systemcodedom-element"></a>\<system.codedom > 元素
指定可用语言提供程序的编译器配置设置。  
  
 \<配置 > 元素  
\<system.codedom > 元素  
  
## <a name="syntax"></a>语法  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<编译器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|编译器配置元素的容器；包含零个或多个 [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 元素。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
  
## <a name="remarks"></a>备注  
  
## <a name="net-framework-version-20"></a>.NET framework 2.0 版  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)元素包含除了如安装.NET Framework 中，使用的默认提供程序的计算机上安装的语言提供程序的编译器配置设置<xref:Microsoft.CSharp.CSharpCodeProvider>和<xref:Microsoft.VisualBasic.VBCodeProvider>。 [\<编译器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)元素包含零个或多[\<编译器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)元素。 每个[\<编译器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)元素指定特定的语言提供程序的编译器配置属性。  
  
 开发人员和编译器供应商可以将配置设置添加到计算机配置文件 (Machine.config) 用于新<xref:System.CodeDom.Compiler.CodeDomProvider>实现。 使用<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>方法以编程方式枚举的默认语言提供程序和语言提供程序标识的计算机上的编译器配置设置。  
  
> [!NOTE]
>  在.NET framework 1.0 和 1.1 中，在标识提供程序由.NET Framework 提供的默认语言[\<编译器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)元素。 在.NET Framework 2.0 版中，默认语言提供程序不识别中[\<编译器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)元素，但可以使用枚举<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>方法。  
  
## <a name="net-framework-versions-10-and-11"></a>.NET framework 1.0 和 1.1 版  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)元素包含的计算机上的语言提供程序的编译器配置设置。 [\<编译器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)元素包含零个或多[\<编译器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)元素。 每个[\<编译器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)元素指定特定的语言提供程序的编译器配置属性。  
  
 .NET Framework 在计算机配置文件 (Machine.config) 中定义初始编译器设置。 开发人员和编译器供应商可以添加新 <xref:System.CodeDom.Compiler.CodeDomProvider> 实现的配置设置。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以编程方式枚举计算机上的语言提供程序和编译器配置设置。  
  
## <a name="configuration-file"></a>配置文件  
 计算机配置文件和应用程序配置文件中，可以使用此元素。  
  
## <a name="example"></a>示例  
 下面的示例演示了典型的编译器配置。  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [编译器和语言提供程序设置架构](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [\<编译器 > 元素](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
