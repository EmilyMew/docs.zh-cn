---
title: Property 过程 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: 47e93ee17f160ce5cd701fd0a12ec16b3997ce9b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828338"
---
# <a name="property-procedures-visual-basic"></a>Property 过程 (Visual Basic)
属性过程是一系列操作模块、 类或结构上的自定义属性的 Visual Basic 语句。 属性过程也被称为*属性访问器*。  
  
 Visual Basic 提供的以下属性过程：  
  
-   一个`Get`过程将返回属性的值。 访问表达式中的属性时调用它。  
  
-   一个`Set`过程将属性设置为某个值，包括的对象引用。 调用时将值分配给属性。  
  
 通常使用的对中定义属性过程`Get`并`Set`语句，但你可以定义单独任一过程，如果该属性是只读的 ([Get 语句](../../../../visual-basic/language-reference/statements/get-statement.md)) 或只写 ([设置语句](../../../../visual-basic/language-reference/statements/set-statement.md))。  
  
 可以省略`Get`和`Set`过程时使用自动实现的属性。 有关详细信息，请参阅[自动实现的属性](./auto-implemented-properties.md)。  
  
 您可以在类、 结构和模块中定义属性。 属性是`Public`默认情况下，这意味着可以从任何位置调用它们的应用程序可以访问该属性的容器中。  
  
 属性和变量的比较，请参阅[属性之间的差异和 Visual Basic 中的变量](./differences-between-properties-and-variables.md)。  
  
## <a name="declaration-syntax"></a>声明语法  
 属性本身定义内包含的代码块[Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)和`End Property`语句。 在此块中，每个属性过程显示为包含在声明语句内的内部块 (`Get`或`Set`) 和匹配`End`声明。  
  
 声明的属性，并且其过程的语法如下所示：  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 `Modifiers`可以指定访问级别和重载、 重写、 共享和隐藏，有关的信息以及该属性是只读或只写。 `AccessLevel`上`Get`或`Set`过程可以为任何级别比属性本身为指定的访问级别限制性更强。 有关详细信息，请参阅[Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)。  
  
### <a name="data-type"></a>数据类型  
 在定义属性的数据类型和主体的访问级别`Property`语句不在属性过程。 属性可以具有一种数据类型。 例如，不能定义属性来存储`Decimal`值，但检索`Double`值。  
  
### <a name="access-level"></a>访问级别  
 但是，可以定义一个属性的主体访问权限级别，并进一步限制所列属性的过程之一中的访问级别。 例如，可以定义`Public`属性，然后定义`Private Set`过程。 `Get`过程保持`Public`。 可以更改属性的过程之一中的访问级别，您可以只是使其比主体的访问级别限制性更强。 有关详细信息，请参阅[如何：声明具有混合的访问级别的属性](./how-to-declare-a-property-with-mixed-access-levels.md)。  
  
## <a name="parameter-declaration"></a>参数声明  
 将每个参数声明为执行操作的相同方式[Sub 过程](./sub-procedures.md)，但必须是传递机制`ByVal`。  
  
 在参数列表中每个参数的语法如下所示：  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 如果参数是可选的您还必须提供一个默认值作为其声明的一部分。 用于指定默认值的语法如下所示：  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>属性值  
 在`Get`过程中，返回值提供给该属性的值调用的表达式。  
  
 在中`Set`过程中，新的属性值传递到参数`Set`语句。 如果显式声明的参数，必须将其声明具有相同的数据类型的属性。 如果未声明的参数，编译器将使用隐式参数`Value`来表示要分配给属性的新值。  
  
## <a name="calling-syntax"></a>调用语法  
 通过使对该属性引用的隐式调用属性过程。 您使用的属性名称为将使用变量的名称的方法相同，只不过必须为不是可选的所有参数提供值，必须将参数列表括在括号中。 如果未不提供任何参数，可以选择性地省略括号。  
  
 隐式调用的语法`Set`过程如下所示：  
  
 `propertyname[(argumentlist)] = expression`  
  
 隐式调用的语法`Get`过程如下所示：  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>声明和调用的插图  
 以下属性将存储为两个构成的名称、 名字和姓氏的完整名称。 当调用代码中读取`fullName`，则`Get`过程组合姓名的两个组成部分，并返回的完整名称。 当调用代码将分配新的完整名称，`Set`过程尝试将其分为两个构成的名称。 如果找不到空间，它将其存储所有为第一个名称。  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 下面的示例演示的属性过程的典型调用`fullName`。  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [Function 过程](./function-procedures.md)
- [运算符过程](./operator-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [在 Visual Basic 中属性和变量之间的差异](./differences-between-properties-and-variables.md)
- [如何：创建属性](./how-to-create-a-property.md)
- [如何：调用 Property 过程](./how-to-call-a-property-procedure.md)
- [如何：声明并在 Visual Basic 中调用默认属性](./how-to-declare-and-call-a-default-property.md)
- [如何：在属性中放置值](./how-to-put-a-value-in-a-property.md)
- [如何：从属性获取一个值](./how-to-get-a-value-from-a-property.md)
