---
title: x:Subclass 指令
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: 850fe8acf9e47149bd385e78b30e04ba77d7a8b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140785"
---
# <a name="xsubclass-directive"></a>x:Subclass 指令
修改 XAML 标记编译行为时`x:Class`还提供了。 而不是创建的分部类的基于`x:Class`，提供`x:Class`中间类，作为创建，然后在提供的派生的类需基于`x:Class`。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`namespace`|可选。 指定一个包含的 CLR 命名空间`classname`。 如果`namespace`指定一个点 （.） 分隔`namespace`和`classname`。|  
|`classname`|必需。 指定连接加载的 XAML 和代码隐藏中为该 XAML 的分部类的 CLR 名称。 请参阅“备注”。|  
|`subclassNamespace`|可选。 可以不同于`namespace`如果每个命名空间可以解析其他。 指定一个包含的 CLR 命名空间`subclassName`。 如果`subclassName`指定一个点 （.） 分隔`subclassNamespace`和`subclassName`。|  
|`subclassName`|必需。 指定子类的 CLR 名称。|  
  
## <a name="dependencies"></a>依赖项  
 [X:class 指令](x-class-directive.md)还必须提供对同一对象，并且该对象必须是 XAML 生产的根元素。  
  
## <a name="remarks"></a>备注  
 `x:Subclass` 使用情况主要适用于不支持分部类声明的语言。  
  
 类用作`x:Subclass`不能为嵌套的类和`x:Subclass`必须引用根对象中的"依赖关系"部分所述。  
  
 否则为概念的含义`x:Subclass`未定义的由.NET Framework XAML 服务实现。 这是因为.NET Framework XAML 服务行为未指定的 XAML 的标记和备份代码已连接的总体编程模型。 与相关的更多概念实现`x:Class`和`x:Subclass`执行的特定框架所使用的编程模型或应用程序模型来定义如何连接 XAML 标记、 编译的标记和基于 CLR 的代码隐藏。 每个框架都可能具有其自己启用某些行为或必须包含在生成环境中的特定组件的生成操作。 在框架中，生成操作也可因特定 CLR 语言用于代码隐藏。  
  
## <a name="wpf-usage-notes"></a>WPF 用法说明  
 `x:Subclass` 可以是页面根元素上或在<xref:System.Windows.Application>在应用程序定义中，其中已经有根`x:Class`。 声明`x:Subclass`之外的页面或应用程序的根，或在不指定它的任何元素`x:Class`存在，则会导致编译时错误。  
  
 创建派生类，这些类为正确`x:Subclass`方案是相当复杂。 您可能需要检查的中间文件 （你的项目的 obj 文件夹中生成的标记编译，其名称合并.xaml 文件名称的.g 文件）。 这些中间文件可以帮助您确定的源的已编译的应用程序中的联接分部类中的某些编程构造。  
  
 在派生类中的事件处理程序必须以`internal override`(`Friend Overrides` Microsoft Visual Basic 中) 若要在编译期间创建中间类中重写的处理程序存根。 否则为派生的类实现隐藏） 的中间类实现，并且不调用中间类处理程序。  
  
 同时定义何时`x:Class`并`x:Subclass`，不需要提供的类的引用的任何实现`x:Class`。 只需为其提供通过名称`x:Class`属性，以便编译器具有中间文件 （编译器不会选择一个默认名称在这种情况下） 中创建的类的一些指导。 可让`x:Class`类实现; 但是，这不是同时使用这二者的典型情景`x:Class`和`x:Subclass`。  
  
## <a name="see-also"></a>请参阅

- [x:Class 指令](x-class-directive.md)
- [XAML 及 WPF 的自定义类](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
