---
title: 对象初始值设定项：命名和匿名类型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 6602a68555e37bf793ba41076ba8f484b4a0dbc3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821343"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>对象初始值设定项：命名和匿名类型 (Visual Basic)
对象初始值设定项，可以使用单个表达式指定为复杂对象的属性。 它们可以用于创建的命名类型和匿名类型的实例。  
  
## <a name="declarations"></a>声明  
 命名和匿名类型的实例的声明可以看起来几乎完全相同，但它们的影响不相同。 每个类别都有其自己的功能和限制。 下面的示例演示方便地声明和初始化已命名的类的实例`Customer`，通过使用对象初始值设定项列表。 请注意，在关键字后指定的类的名称是`New`。  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 匿名类型已没有可用的名称。 因此的匿名类型实例化不能包含类名。  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 要求和结果的两个声明都不相同。 有关`namedCust`、 一个`Customer`具有类`Name`属性必须已经存在，并且声明会创建该类的实例。 有关`anonymousCust`，编译器会定义一个新类，具有一个属性，一个字符串称为`Name`，并创建该类的新实例。  
  
## <a name="named-types"></a>命名的类型  
 对象初始值设定项提供一种简单方法调用一种类型的构造函数，然后在单个语句中设置某些或所有属性的值。 编译器将调用该语句的适当构造函数： 默认构造函数，如果未不提供任何参数或如果发送一个或多个实参的参数化构造函数。 然后，指定的属性的初始值设定项列表中出现的顺序初始化。  
  
 初始值设定项列表中的每个初始化包含的类的成员初始值分配。 定义类时确定的名称和数据类型的成员。 在以下示例中，`Customer`类必须存在，并且必须具有成员命名`Name`和`City`，可以接受字符串值。  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 或者，可以使用以下代码来获取相同的结果：  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 每个这些声明是等效于以下示例中，这会创建`Customer`通过使用默认构造函数中，对象，然后指定初始值`Name`并`City`属性使用`With`语句。  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 如果`Customer`类包含使你能够发送中的值的参数化构造函数`Name`，例如，您可以声明和初始化`Customer`对象中的以下方法：  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 无需初始化所有属性，如以下代码所示。  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 但是，在初始化列表不能为空。 未初始化的属性保留其默认值。  
  
### <a name="type-inference-with-named-types"></a>使用命名类型的类型推理  
 您可以缩短的声明代码`cust1`通过组合对象初始值设定项和局部类型推理。 这使您可以省略`As`变量声明中的子句。 从创建由赋值的对象的类型推断该变量的数据类型。 在下面的示例中，类型`cust6`是`Customer`。  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>有关命名类型的备注  
  
-   不能在对象初始值设定项列表中的多个时间初始化类成员。 声明`cust7`将导致错误。  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
-   成员可用于初始化自身或另一个字段。 如果之前尚未初始化，如下所示的以下声明访问成员`cust8`，将使用默认值。 请记住，使用对象初始值设定项的声明，处理时，第一件事是调用适当的构造函数。 之后，将初始化初始值设定项列表中的各个字段。 下面的示例中的默认值为`Name`分配给`cust8`，并已初始化的值分配`cust9`。  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     下面的示例使用从参数化构造函数`cust3`并`cust4`来声明和初始化`cust10`和`cust11`。  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
-   可以嵌套对象初始值设定项。 在以下示例中，`AddressClass`是具有两个属性的类`City`并`State`，和`Customer`类具有`Address`的实例的属性`AddressClass`。  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
-   初始化列表不能为空。  
  
-   正在初始化的实例不能是类型对象。  
  
-   正在初始化类成员不能为共享的成员、 只读成员、 常量或方法调用。  
  
-   正在初始化类成员不能编制索引，或限定。 下面的示例引发编译器错误：  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>匿名类型  
 匿名类型使用对象初始值设定项来创建未显式定义的新类型和名称的实例。 相反，编译器将生成在对象初始值设定项列表根据你指定的属性的类型。 由于未指定类型的名称，因此将它称为*匿名类型*。 例如，比较下面的声明与上一为`cust6`。  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 唯一的区别语法上是后未指定任何名称`New`的数据类型。 但是，会发生什么情况却大相径庭。 编译器会定义新的匿名类型具有两个属性`Name`和`City`，并使用指定的值创建它的一个实例。 类型推导用于确定的类型`Name`和`City`在示例中为字符串。  
  
> [!CAUTION]
>  匿名类型的名称由编译器、 生成和编译的而有所不同。 你的代码不应使用或依赖于的匿名类型的名称。  
  
 类型的名称不可用，因为不能使用`As`子句来声明`cust13`。 必须推断其类型。 如果不使用后期绑定，这将限制到本地变量的匿名类型的使用。  
  
 匿名类型提供对关键支持[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查询。 有关使用查询中的匿名类型的详细信息，请参阅[匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)并[在 Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
### <a name="remarks-about-anonymous-types"></a>有关匿名类型的备注  
  
-   通常，所有或大多数匿名类型声明中的属性将是键属性，通过键入关键字指示`Key`属性名称的前面。  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     键属性的详细信息，请参阅[密钥](../../../../visual-basic/language-reference/modifiers/key.md)。  
  
-   如已命名的类型，初始值设定项列表的匿名类型定义必须声明至少一个属性。  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
-   当声明匿名类型的实例时，编译器将生成匹配的匿名类型定义。 名称和数据类型的属性来自实例声明中，并由编译器在定义中包含。 属性不是名为，将为命名类型，请提前定义。 其类型推断。 不能通过使用指定的属性的数据类型`As`子句。  
  
-   匿名类型也可以建立的名称和其属性的值采用一些其他方法。 例如，匿名类型属性可能需要的名称和变量，或名称的值和另一个对象的属性的值。  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     有关定义匿名类型中的属性的选项的详细信息，请参阅[如何：推断属性名和匿名类型声明中的类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
## <a name="see-also"></a>请参阅

- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [如何：推断属性名和匿名类型声明中的类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
- [如何：使用对象初始值设定项声明对象](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
