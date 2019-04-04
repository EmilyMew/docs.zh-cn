---
title: 后期绑定解决方案；可能会发生运行时错误
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 4fe79c74b6ff634223a4f10d8c5dc54bb77571cc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822249"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>后期绑定解决方案；可能会发生运行时错误
一个对象分配给声明为变量[Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)。  
  
 当你声明一个变量，作为`Object`，编译器必须执行*后期绑定*，这将导致在运行时产生额外的操作。 它还使应用程序易于发生潜在的运行时错误。 例如，如果你将分配<xref:System.Windows.Forms.Form>到`Object`变量，然后尝试访问<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType>属性，则运行时会引发<xref:System.MemberAccessException>因为<xref:System.Windows.Forms.Form>类不公开`NameTable`属性。  
  
 如果声明为特定类型的变量，编译器可以执行*早期绑定*在编译时。 这会导致改进性能，受控访问的特定类型的成员和提高代码的可读性。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **错误 ID:** BC42017  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   如果可能，声明为特定类型的变量。  
  
## <a name="see-also"></a>请参阅

- [早期绑定和后期绑定](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [对象变量声明](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
