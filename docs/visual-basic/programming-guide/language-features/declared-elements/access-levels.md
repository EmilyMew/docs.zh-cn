---
title: Visual Basic 中的访问级别
ms.date: 05/10/2018
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private Protected access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: d8f2f16d2fb15f2e840f13f177d3fea83fda315e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843085"
---
# <a name="access-levels-in-visual-basic"></a>Visual Basic 中的访问级别
*访问级别*已声明元素的是能够对其进行访问的程度，哪些代码，即有权读取或写入到它。 这确定不仅元素本身; 的声明方式，还通过元素的容器的访问级别。 无法访问包含元素的代码无法访问任何其包含的元素，甚至包括那些声明为`Public`。 例如，`Public`变量中`Private`结构可以从访问，在类中包含的结构，但不能从该类的外部。  
  
## <a name="public"></a>Public  
 [公共](../../../../visual-basic/language-reference/modifiers/public.md)关键字声明语句中的指定从同一个项目中的任意位置的代码、 其他引用该项目的项目和项目生成任何程序集，可访问元素。 下面的代码显示了一个示例`Public`声明。  
  
```vb  
Public Class classForEverybody  
```  
  
 可以使用`Public`仅在模块、 接口或命名空间级别。 这意味着您可以声明的源文件或命名空间，或在接口、 模块、 类或结构，但不是能在过程级别的公共元素。  
  
## <a name="protected"></a>Protected  
 [受保护](../../../../visual-basic/language-reference/modifiers/protected.md)关键字声明语句中的指定该元素可以访问只能从中，在同一类中，或从此类派生的类。 下面的代码显示了一个示例`Protected`声明。  
  
```vb  
Protected Class classForMyHeirs  
```  
  
 可以使用`Protected`只能在类级别并且仅当你声明类的成员。 这意味着您可以声明受保护的元素在类中，但不是能在级别的源文件或命名空间，或在接口、 模块、 结构或过程。  
  
## <a name="friend"></a>Friend  
 [友元](../../../../visual-basic/language-reference/modifiers/friend.md)关键字声明语句中的指定同一程序集中，但不能从该元素可以从访问程序集外部的。 下面的代码显示了一个示例`Friend`声明。  
  
```vb  
Friend stringForThisProject As String  
```  
  
 可以使用`Friend`仅在模块、 接口或命名空间级别。 这意味着您可以声明的源文件或命名空间，或在接口、 模块、 类或结构，但不是能在过程级别的友元元素。  
  
## <a name="protected-friend"></a>受保护的友元  
 [Protected Friend](../../../language-reference/modifiers/protected-friend.md)声明语句中的关键字组合指定从派生类或中，可以访问元素和 / 或同一程序集。 下面的代码显示了一个示例`Protected Friend`声明。  
  
```vb  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 可以使用`Protected Friend`只能在类级别并且仅当你声明类的成员。 这意味着您可以声明为 protected 的 friend 元素在类中，但不是能在级别的源文件或命名空间，或在接口、 模块、 结构或过程。  
  
## <a name="private"></a>Private  
 [专用](../../../../visual-basic/language-reference/modifiers/private.md)关键字声明语句中的指定只能从相同模块、 类或结构中，可以访问该元素。 下面的代码显示了一个示例`Private`声明。  
  
```vb  
Private numberForMeOnly As Integer  
```  
  
 只能在模块级别使用 `Private`。 这意味着可以声明一个私有元素在模块、 类或结构，而不是在源文件或命名空间，在一个接口，或在过程中的级别。  
  
 在模块级别`Dim`而无需任何访问级别关键字的语句是等效于`Private`声明。 但是，你可能想要使用`Private`关键字来使代码更易于阅读和理解。  

## <a name="private-protected"></a>专用受保护

[Private Protected](../../../language-reference/modifiers/private-protected.md)声明语句中的关键字组合指定元素，可仅从在同一类中，以及从派生类中包含的类相同的程序集中找到访问。 `Private Protected` Visual Basic 15.5 开始支持访问修饰符。

下面的示例演示`Private Protected`声明：

```vb
Private Protected internalValue As Integer
```

您可以声明`Private Protected`仅在一个类内部的元素。 不能将其声明中的接口或结构，也可以将其声明的源文件或命名空间，内部接口或结构，或在过程中的级别。

`Private Protected`由 Visual Basic 15.5 和更高版本提供支持访问修饰符。 若要使用它，您将以下元素添加到 Visual Basic 项目 (*.vbproj) 文件。 只要 Visual Basic 15.5 或更高版本在系统上安装的因为它允许您充分利用所有最新版本的 Visual Basic 编译器支持的语言功能：

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

若要使用`Private Protected`访问修饰符，必须将以下元素添加到 Visual Basic 项目 (*.vbproj) 文件：

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

有关详细信息请参阅[设置的 Visual Basic 语言版本](../../../language-reference/configure-language-version.md)。

## <a name="access-modifiers"></a>访问修饰符  

指定的访问级别的关键字称为*访问修饰符*。 下表比较了访问修饰符。  
  
|访问修饰符|授予的访问级别|您可以使用此访问级别声明的元素|可以在其中使用此修饰符声明上下文|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|不受限制:<br /><br /> 任何可以看到公共元素的代码可以访问它|接口<br /><br /> 模块<br /><br /> 类<br /><br /> 结构<br /><br /> 结构成员<br /><br /> 过程<br /><br /> 属性<br /><br /> 成员变量<br /><br /> 常量<br /><br /> 枚举<br /><br /> 事件<br /><br /> 外部声明<br /><br /> 委托|源文件<br /><br /> 命名空间<br /><br /> 接口<br /><br /> 模块<br /><br /> 类<br /><br /> 结构|  
|`Protected`|追溯时派生：<br /><br /> 声明为受保护的元素或由其派生的类可以访问的元素的类中的代码|接口<br /><br /> 类<br /><br /> 结构<br /><br /> 过程<br /><br /> 属性<br /><br /> 成员变量<br /><br /> 常量<br /><br /> 枚举<br /><br /> 事件<br /><br /> 外部声明<br /><br /> 委托|类|  
|`Friend`|程序集：<br /><br /> 代码中声明的友元元素可以访问它的程序集|接口<br /><br /> 模块<br /><br /> 类<br /><br /> 结构<br /><br /> 结构成员<br /><br /> 过程<br /><br /> 属性<br /><br /> 成员变量<br /><br /> 常量<br /><br /> 枚举<br /><br /> 事件<br /><br /> 外部声明<br /><br /> 委托|源文件<br /><br /> 命名空间<br /><br /> 接口<br /><br /> 模块<br /><br /> 类<br /><br /> 结构|  
|`Protected` `Friend`|联合的`Protected`和`Friend`:<br /><br /> 在同一个类或作为受保护的友元元素或元素的类派生的任何类中的相同程序集代码中，可以访问它|接口<br /><br /> 类<br /><br /> 结构<br /><br /> 过程<br /><br /> 属性<br /><br /> 成员变量<br /><br /> 常量<br /><br /> 枚举<br /><br /> 事件<br /><br /> 外部声明<br /><br /> 委托|类|  
|`Private`|声明上下文：<br /><br /> 声明一个私有元素，包括代码中包含的类型，可以访问的元素的类型中的代码|接口<br /><br /> 类<br /><br /> 结构<br /><br /> 结构成员<br /><br /> 过程<br /><br /> 属性<br /><br /> 成员变量<br /><br /> 常量<br /><br /> 枚举<br /><br /> 事件<br /><br /> 外部声明<br /><br /> 委托|模块<br /><br /> 类<br /><br /> 结构|
|`Private Protected`|声明一个私有受保护的元素，在类中的代码或作为 bas 类在同一程序集中找到的派生类中的代码。|接口<br /><br /> 类<br /><br /> 结构<br /><br /> 过程<br /><br /> 属性<br /><br /> 成员变量<br /><br /> 常量<br /><br /> 枚举<br /><br /> 事件<br /><br /> 外部声明<br /><br /> 委托|类|
  
## <a name="see-also"></a>请参阅

- [Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
- [已声明的元素名称](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [已声明元素的特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [在 Visual Basic 中的生存期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [在 Visual Basic 中的作用域](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [如何：控制变量的可用性](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)
- [变量](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
