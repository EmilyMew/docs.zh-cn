---
title: 如何：访问对象 (Visual Basic 中) 的成员
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 2b7e600a23ed326fe3e914957b4e698bc34c6135
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819641"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>如何：访问对象 (Visual Basic 中) 的成员
引用的对象的对象变量后，你通常想要与该对象，例如其方法、 属性、 字段和事件的成员。 例如，一次创建一个新<xref:System.Windows.Forms.Form>对象，你可能想要设置其<xref:System.Windows.Forms.Control.Text%2A>属性或调用其<xref:System.Windows.Forms.Control.Focus%2A>方法。  
  
## <a name="accessing-members"></a>成员访问  
 通过对引用该变量访问对象的成员。  
  
#### <a name="to-access-members-of-an-object"></a>若要访问对象的成员  
  
-   使用成员访问运算符 (`.`) 之间的对象变量名称和成员名称。  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     如果该成员是[共享](../../../../visual-basic/language-reference/modifiers/shared.md)，不需要一个变量来访问它。  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>已知类型的对象的成员访问  
 如果在编译时知道对象的类型，则可以使用*早期绑定*指的是它的变量。  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>若要访问的对象，您知道该类型在编译时成员  
  
1.  你想要分配给该变量的对象类型的对象变量声明。  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     与`Option Strict On`，可以仅将分配<xref:System.Windows.Forms.Form>对象 (或类型的对象派生自<xref:System.Windows.Forms.Form>) 到`extraForm`。 如果已定义的类或结构优先于具有拓宽`CType`转换为<xref:System.Windows.Forms.Form>，还可以将该类或结构`extraForm`。  
  
2.  使用成员访问运算符 (`.`) 之间的对象变量名称和成员名称。  
  
    ```  
    extraForm.Show()  
    ```  
  
     您可以访问的所有方法和属性特定于<xref:System.Windows.Forms.Form>类，无论什么`Option Strict`设置。  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>未知类型的对象的成员访问  
 如果在编译时不知道对象的类型，则必须使用*后期绑定*它是指任何变量。  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>若要访问的对象为其您不知道该类型在编译时成员  
  
1.  对象变量的声明[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)。 (声明一个变量，作为`Object`等同于其声明为<xref:System.Object?displayProperty=nameWithType>。)  
  
    ```  
    Dim someControl As Object  
    ```  
  
     与`Option Strict On`，可以访问成员上定义的<xref:System.Object>类。  
  
2.  使用成员访问运算符 (`.`) 之间的对象变量名称和成员名称。  
  
    ```  
    someControl.GetType()  
    ```  
  
     若要能够访问分配给对象变量的任何对象的成员，必须设置`Option Strict Off`。 当执行此操作时，编译器无法保证给定的成员由分配给变量的对象。 如果对象未公开的成员尝试访问，<xref:System.MemberAccessException>会发生异常。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [对象变量声明](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object 数据类型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
