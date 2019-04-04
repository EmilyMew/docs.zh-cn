---
title: 此“Sub New”的第一条语句必须是对“MyBase.New”或“MyClass.New”的显式调用，因为“<constructorname>”的基类“<baseclassname>”中的“<derivedclassname>”被标记为已过时：“<errormessage>”
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 737f9119814e784ebabcbb4629ab6948ce164168
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814089"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a>此 Sub New 的第一个语句必须是对 MyBase.New 或 MyClass.New 的显式调用，因为\<constructorname > 在基类的\<a m e >' 的 '\<derivedclassname > 标记为已过时:\<错误消息 >'
类构造函数不显式调用基类构造函数，并且隐式基类构造函数标有 <xref:System.ObsoleteAttribute> 特性和将其视为错误的指令。  
  
 当在派生的类构造函数未调用基类构造函数时，Visual Basic 将尝试生成对无参数基类构造函数的隐式调用。 如果可以调用不带参数的基类中没有任何可访问的构造函数，Visual Basic 不能生成的隐式调用。 在这种情况下，所需的构造函数标有<xref:System.ObsoleteAttribute>属性，因此 Visual Basic 不能调用它。  
  
 可以通过将 <xref:System.ObsoleteAttribute> 应用于任意编程元素，将其标记为不再使用。 如果执行此操作，则可以将特性的 <xref:System.ObsoleteAttribute.IsError%2A> 属性设置为 `True` 或 `False`。 如果设置为 `True`，则编译器将尝试使用该元素的操作视为错误。 如果设置为 `False`，或让它默认为 `False`，则编译器会在尝试使用该元素时发出警告。  
  
 **错误 ID:** BC30920  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  检查引用的错误信息并采取相应的操作。  
  
2.  将对 `MyBase.New()` 或 `MyClass.New()` 的调用包括为派生类中 `Sub New` 的第一个语句。  
  
## <a name="see-also"></a>请参阅

- [属性概述](../../../visual-basic/programming-guide/concepts/attributes/index.md)
