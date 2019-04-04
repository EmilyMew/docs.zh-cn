---
title: 自定义 My 中可用的对象 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: c0b47521c6a62071466ae4193cd8553bdfb3dcde
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890366"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>自定义 My 中可用的对象 (Visual Basic)

本主题介绍如何控制哪些`My`通过设置你的项目启用对象`_MYTYPE`条件编译常量。 Visual Studio 集成开发环境 (IDE) 使`_MYTYPE`条件编译常量与项目的类型同步项目。  
  
## <a name="predefined-mytype-values"></a>预定义的\_MYTYPE 值  

必须使用`/define`编译器选项来设置`_MYTYPE`条件编译常量。 指定自己的值时`_MYTYPE`常量，您必须将字符串值中反斜杠/英文引号连用 (\\") 序列。 例如，可以使用：  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 此表显示了什么`_MYTYPE`条件编译常量设置为多个项目类型。  
  
|项目类型|\_MYTYPE 值|  
|------------------|--------------------|  
|类库|"Windows"|  
|控制台应用程序|"控制台"|  
|Web|"Web"|  
|Web 控件库|"WebControl"|  
|Windows 应用程序|"WindowsForms"|  
|Windows 应用程序中，使用的自定义启动时 `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Windows 控件库|"Windows"|  
|Windows 服务|"控制台"|  
|空|"空"|  
  
> [!NOTE]
> 所有条件编译字符串比较都是区分大小写，而不考虑如何`Option Compare`语句设置。  
  
## <a name="dependent-my-compilation-constants"></a>依赖\_我编译常量  

`_MYTYPE`条件编译常量，反过来，控制的其他几个值`_MY`编译常量：  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"控制台"|"控制台"|"Windows"|未定义|"Windows"|true|  
|"自定义"|未定义|未定义|未定义|未定义|未定义|  
|"空"|未定义|未定义|未定义|未定义|未定义|  
|"Web"|未定义|"Web"|false|"Web"|false|  
|"WebControl"|未定义|"Web"|false|"Web"|true|  
|"Windows"或""|"Windows"|"Windows"|未定义|"Windows"|true|  
|"WindowsForms"|"WindowsForms"|"Windows"|true|"Windows"|true|  
|"WindowsFormsWithCustomSubMain"|"控制台"|"Windows"|true|"Windows"|true|  
  
 默认情况下，未定义的条件编译常量解析为`FALSE`。 编译你的项目以重写默认行为时，可以指定未定义的常量值。  
  
> [!NOTE]
> 当`_MYTYPE`设置为"Custom"，该项目包含`My`命名空间，但它不包含任何对象。 但是，将设置`_MYTYPE`到"空"，则会阻止编译器添加`My`命名空间及其对象。  
  
 此表描述了预定义值的效果`_MY`编译常量。  
  
|返回的常量|含义|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|使`My.Application`，该常量不在"控制台，"Windows，如果"或"WindowsForms":<br /><br /> 的派生自"控制台"版本<xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>。 并且具有比"Windows"的版本较少的成员。<br />"Windows"版本派生<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>和具有比"WindowsForms"版本较少的成员。<br />-"WindowsForms"版本`My.Application`派生自<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>。 如果`TARGET`常量被定义为"winexe"，然后该类包括`Sub Main`方法。|  
|`_MYCOMPUTERTYPE`|使`My.Computer`，则该常量不在"Web"或"Windows":<br /><br /> "Web"版本派生<xref:Microsoft.VisualBasic.Devices.ServerComputer>，并且具有比"Windows"的版本较少的成员。<br />-的"Windows"新版`My.Computer`派生自<xref:Microsoft.VisualBasic.Devices.Computer>。|  
|`_MYFORMS`|使`My.Forms`，则该常量不在`TRUE`。|  
|`_MYUSERTYPE`|使`My.User`，则该常量不在"Web"或"Windows":<br /><br /> -的版本"Web"`My.User`与当前的 HTTP 请求的用户标识相关联。<br />-的版本"Windows"`My.User`与线程的当前主体相关联。|  
|`_MYWEBSERVICES`|使`My.WebServices`，则该常量不在`TRUE`。|  
|`_MYTYPE`|使`My.Log`， `My.Request`，和`My.Response`，则该常量不在"Web"。|  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My 对项目类型的依赖方式](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [条件编译](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms 对象](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request 对象](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response 对象](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices 对象](../../../visual-basic/language-reference/objects/my-webservices-object.md)
