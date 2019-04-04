---
title: Visual Basic 中的 Me、My、MyBase 和 MyClass
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: a8df6e48fd5bce9bb28d8aef7e031f36741ad0ad
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813387"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic 中的 Me、My、MyBase 和 MyClass
`Me``My`， `MyBase`，和`MyClass`在 Visual Basic 中具有类似名称，但不同的用途。 本主题介绍上述每个实体以将它们区分开来。  
  
## <a name="me"></a>Me  
 `Me`关键字提供了一种方法来指代类或当前正在其中执行代码的结构的特定实例。 `Me` 行为类似于的对象变量或结构变量引用当前实例。 使用`Me`特别适合将类或结构的当前正在执行的实例的信息传递给另一个类、 结构或模块中的过程。  
  
 例如，假设在模块中有下面的过程。  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 可以调用此过程，并将传递的当前实例<xref:System.Windows.Forms.Form>作为通过使用以下语句参数的类。  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 `My`功能提供对许多比较容易、 直观访问[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]类，使 Visual Basic 用户与计算机、 应用程序、 设置、 资源等进行交互。  
  
## <a name="mybase"></a>MyBase  
 `MyBase`关键字的行为类似于一个类的当前实例的基类引用的对象变量。 `MyBase` 通常用于访问基类成员被重写或派生类中被隐藏。 `MyBase.New` 用于从派生的类构造函数中显式调用基类构造函数。  
  
## <a name="myclass"></a>MyClass  
 `MyClass`关键字的行为类似于与最初实现的类的当前实例引用的对象变量。 `MyClass` 类似于`Me`，但方法是在其上的所有方法调用都被都看作`NotOverridable`。  
  
## <a name="see-also"></a>请参阅

- [继承的基础知识](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
