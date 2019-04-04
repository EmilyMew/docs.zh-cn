---
title: 匿名类型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: 3dc2083e5b4fd06250a1387c32f0eba28e879b30
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829130"
---
# <a name="anonymous-types-visual-basic"></a>匿名类型 (Visual Basic)
Visual Basic 支持匿名类型，以便你能够而无需编写的数据类型的类定义创建对象。 此时，编译器将为你生成类。 类已没有可用的名称，直接继承自<xref:System.Object>，且包含在声明该对象指定的属性。 由于未指定数据类型的名称，因此将它称为*匿名类型*。  
  
 以下示例声明并创建变量`product`视为具有两个属性的匿名类型的实例`Name`和`Price`。  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 一个*查询表达式*使用匿名类型将合并的查询所选择的数据列。 因为无法预测的特定查询可能选择的列，不能提前，定义结果的类型。 匿名类型，可以编写选择任意数量的列，按任意顺序的查询。 编译器创建的数据类型与指定的属性和指定的顺序匹配。  
  
 在以下示例中，`products`是一系列产品对象，其中每个有许多属性。 变量`namePriceQuery`保存的查询在执行时返回的实例具有两个属性的匿名类型集合的定义`Name`和`Price`。  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 变量`nameQuantityQuery`保存的查询在执行时返回的实例具有两个属性的匿名类型集合的定义`Name`和`OnHand`。  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 有关创建由编译器为匿名类型的代码的详细信息，请参阅[匿名类型定义](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。  
  
> [!CAUTION]
>  匿名类型的名称是编译器生成和编译的而有所不同。 你的代码不应使用或依赖的匿名类型的名称，因为重新编译项目时，可能会更改名称。  
  
## <a name="declaring-an-anonymous-type"></a>声明匿名类型  
 匿名类型的实例的声明使用初始值设定项列表来指定类型的属性。 当你声明匿名类型、 不其他类元素，如方法或事件时，可以指定仅属性。 在以下示例中，`product1`是具有两个属性的匿名类型的实例：`Name`和`Price`。  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 如果将属性指定为键属性，可以使用它们来比较两个匿名类型实例相等。 但是，不能更改键属性的值。 请参阅后面本主题的详细信息的键属性部分。  
  
 请注意，声明匿名类型的实例是类似于通过使用对象初始值设定项声明命名类型的实例：  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 有关指定匿名类型属性的其他方法的详细信息，请参阅[如何：推断属性名和匿名类型声明中的类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
## <a name="key-properties"></a>键属性  
 键属性不同于非键属性多个重要方面：  
  
-   只有键属性的值进行比较以确定两个实例是否相等。  
  
-   键属性的值是只读的并且不能更改。  
  
-   仅匿名类型的编译器生成的哈希代码算法中包括键属性值。  
  
### <a name="equality"></a>相等  
 匿名类型的实例可以是同一匿名类型的实例才相等。 编译器将两个实例视为相同类型的实例，如果满足以下条件：  
  
-   在同一程序集中声明它们。  
  
-   它们的属性具有相同的名称相同的推断类型和声明顺序相同。 名称比较不区分大小写。  
  
-   在每个相同的属性都标记为键属性。  
  
-   每个声明中的至少一个属性是键属性。  
  
 具有任何键属性的匿名类型的实例是只等于其自身。  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 如果其键属性的值相等，则同一匿名类型的两个实例相等。 以下示例说明了如何测试相等。  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>只读的值  
 不能更改键属性的值。 例如，在`prod8`在上一示例中，`Name`并`Price`字段`read-only`，但`OnHand`可以更改。  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a>查询表达式中的匿名类型  
 查询表达式始终不需要创建匿名类型。 如果可能，它们使用现有类型以保存列数据。 查询从数据源或每条记录中的只有一个字段返回任一整条记录时，将发生这种情况。 在下面的代码示例中，`customers`是一系列的对象`Customer`类。 类具有许多属性，并可在查询结果中，按任意顺序包含一个或多个。 在前两个示例中，任何匿名类型不是必需，因为查询中选择的命名类型的元素：  
  
-   `custs1` 包含一系列字符串，因为`cust.Name`是一个字符串。  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
-   `custs2` 包含一系列`Customer`对象，因为每个元素的`customers`是`Customer`查询选择对象，并且整个元素。  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 但是，相应的命名的类型并非始终可用。 您可能想要选择客户名称和地址的一种用途、 客户 ID 号和位置，以及客户名称、 地址和订单历史记录中的第三个。 匿名类型，可选择任意组合的属性，按任意顺序，而无需第一个声明新的命名的类型以保存结果。 相反，编译器会创建每个编译属性的匿名类型。 以下查询从每个选择仅客户的姓名和 ID 号`Customer`对象中`customers`。 因此，编译器会创建包含仅这两个属性的匿名类型。  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 名称和匿名类型中的属性的数据类型执行的参数从`Select`，`cust.Name`和`cust.ID`。 由查询创建的匿名类型中的属性始终是键属性。 当`custs3`在下面的示例执行`For Each`循环中，结果是具有两个键属性的匿名类型的实例的集合`Name`和`ID`。  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 表示的集合中的元素`custs3`强类型，以及您可以使用 IntelliSense 来浏览可用的属性和以验证它们的类型。  
  
 有关详细信息，请参阅[Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>确定是否使用匿名类型  
 作为匿名类的实例创建对象之前，请考虑这是否是最佳选择。 例如，如果你想要创建临时对象，以包含相关的数据，并且具有无需其他字段和完整的类可能包含的方法，匿名类型是一个不错的解决方案。 如果你想选择不同的属性对于每个声明，或如果你想要更改属性的顺序，匿名类型是还方便。 但是，如果你的项目包含几个对象有相同的属性，按固定顺序，您可以声明它们更轻松地通过类构造函数中使用命名的类型。 例如，与相应的构造函数，它是更轻松地声明的多个实例`Product`类不是它是声明匿名类型的多个实例。  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 命名类型的另一个优点是编译器可以捕获属性名称的无意拼写错误。 在上一示例中， `firstProd2`， `secondProd2`，和`thirdProd2`都应是相同的匿名类型的实例。 但是，如果您意外声明`thirdProd2`通过以下方式之一，其类型应为不同于`firstProd2`和`secondProd2`。  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 更重要的是，有的不适用于已命名类型的实例的匿名类型的使用限制。 `firstProd2``secondProd2`，和`thirdProd2`是相同的匿名类型的实例。 但是，共享的匿名类型的名称不可用，并且不能出现在代码中预期的类型名称的。 例如，匿名类型不能用于定义方法签名，若要声明另一个变量或字段，或任何类型声明中。 因此，如果您不得不在方法之间共享的信息匿名类型不适合。  
  
## <a name="an-anonymous-type-definition"></a>匿名类型定义  
 在响应的匿名类型的实例声明时，编译器会创建包含指定的属性的新类定义。  
  
 如果匿名类型包含至少一个键属性，定义将重写继承的三个成员<xref:System.Object>: <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。 代码生成测试相等性，并确定哈希代码值将视为仅的键属性。 如果匿名类型包含任何键属性，仅<xref:System.Object.ToString%2A>被重写。 显式命名的匿名类型属性不能与这些生成的方法发生冲突。 也就是说，不能使用`.Equals`， `.GetHashCode`，或`.ToString`命名属性。  
  
 具有至少一个匿名类型定义的键属性还实现<xref:System.IEquatable%601?displayProperty=nameWithType>接口，其中`T`是匿名类型的类型。  
  
 有关由编译器和重写方法的功能创建的代码的详细信息，请参阅[匿名类型定义](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。  
  
## <a name="see-also"></a>请参阅

- [对象初始值设定项：命名和匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [如何：推断属性名和匿名类型声明中的类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [匿名类型定义](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
