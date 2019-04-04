---
title: 基本查询操作 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: ed5ed56366911c3676c4413711207ac0a8f85765
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826192"
---
# <a name="basic-query-operations-visual-basic"></a>基本查询操作 (Visual Basic)
本主题提供了简要介绍了[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]表达式在 Visual Basic 中和某些典型查询中执行的操作。 有关详细信息，请参阅下列主题：  
  
 [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [查询](../../../../visual-basic/language-reference/queries/index.md)  
  
 [演练：在 Visual Basic 中编写查询](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>指定数据源 (From)  
 在[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查询，第一步是指定您想要查询的数据源。 因此，`From`在查询中的子句始终第一个出现。 查询运算符选择，并基于源的类型结果的形式。  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 `From`子句指定数据源`customers`，和一个*范围变量*， `cust`。 范围变量类似于循环迭代变量，只是在查询表达式中，不会真正发生迭代。 执行查询时，通常通过使用`For Each`循环中，范围变量可作为对中的每个后续元素的引用`customers`。 由于编译器可以推断 `cust` 的类型，因此无需显式指定它。 有关编写使用和不使用显式类型化的查询的示例，请参阅[查询操作 (Visual Basic 中) 中的类型关系](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。  
  
 有关如何使用详细信息`From`子句在 Visual Basic 中，请参阅[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)。  
  
## <a name="filtering-data-where"></a>筛选数据 （位置）  
 可能的最常见的查询操作应用形式的布尔表达式筛选器。 然后，查询将返回仅对表达式为 true 的元素。 一个`Where`子句用来执行筛选。 筛选器指定要生成序列中包含的数据源中的哪些元素。 在以下示例中，仅那些具有地址位于伦敦客户包含。  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 您可以使用逻辑运算符，如`And`并`Or`合并筛选器表达式中的`Where`子句。 例如，若要返回来自伦敦谁是，其名称为 Devon 客户，请使用以下代码：  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 若要返回来自 London 或 Paris 的客户，使用以下代码：  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 有关如何使用详细信息`Where`子句在 Visual Basic 中，请参阅[Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)。  
  
## <a name="ordering-data-order-by"></a>对数据 (Order By) 进行排序  
 它通常是可以方便地对返回的数据按特定顺序进行排序。 `Order By`子句会使返回按指定的一个或多个字段进行排序的序列中的元素。 例如，以下查询对基于对结果进行排序`Name`属性。 因为`Name`是一个字符串，返回的数据将从 A 到 Z 的字母顺序，排序。  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 要对结果进行从 Z 到 A 的逆序排序，请使用 `Order By...Descending` 子句。 默认值是`Ascending`当没有`Ascending`也不`Descending`指定。  
  
 有关如何使用详细信息`Order By`子句在 Visual Basic 中，请参阅[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
## <a name="selecting-data-select"></a>选择数据 （选择）  
 `Select`子句指定的窗体和返回的元素的内容。 例如，可以指定您的结果将包含的是整个`Customer`对象，只是一个`Customer`基于计算属性、 属性的子集，从各种数据源或一些新的结果类型的属性的组合。 当 `Select` 子句生成除源元素副本以外的内容时，该操作称为投影。  
  
 检索一个集合，其中包含完整`Customer`对象，选择的范围变量本身：  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 如果`Customer`实例是具有许多字段、 一个大型对象和所有你想要检索是的名称，可以选择`cust.Name`，如以下示例所示。 局部类型推理知道此集合中的更改的结果类型`Customer`到字符串的集合对象。  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 若要选择多个字段从数据源，您有两种选择：  
  
-   在`Select`子句中，指定你想要在结果中包含的字段。 编译器将定义这些字段作为其属性的匿名类型。 有关详细信息，请参阅[匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
     在下面的示例返回的元素为匿名类型的实例，因为你不能为类型根据名称引用其他位置在代码中。 编译器指定的类型名称包含不正常的 Visual Basic 代码中有效的字符。 在下面的示例中的查询返回的集合中的元素`londonCusts4`是匿名类型的实例  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     或  
  
-   定义包含你想要包括在结果中，创建并初始化在类型的实例的特定字段的命名的类型`Select`子句。 仅当您必须使用各个结果集合外部的顺序返回它们，或如果您需要将它们作为方法调用中的参数传递，请使用此选项。 类型`londonCusts5`在下面的示例是 IEnumerable (Of NamePhone)。  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 有关如何使用详细信息`Select`子句在 Visual Basic 中，请参阅[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。  
  
## <a name="joining-data-join-and-group-join"></a>联接数据 （联接和分组联接）  
 你可以组合多个数据源中的`From`几种方式的子句。 例如，以下代码使用两个数据源，并从它们在结果中属性隐式组合在一起。 该查询用于选择的学生以元音开头的姓氏和名字。  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
>  您可以运行此代码中创建的学生列表[如何：创建的项列表](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。  
  
 `Join`关键字等效于`INNER JOIN`SQL 中。 它结合了两个集合根据两个集合中元素之间的匹配项的值。 查询将返回具有匹配的键值对集合元素的全部或部分。 例如，下面的代码复制上一个隐式联接操作。  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join` 将集合合并为单个分层集合，就像`LEFT JOIN`SQL 中。 有关详细信息，请参阅[Join 子句](../../../../visual-basic/language-reference/queries/join-clause.md)并[Group Join 子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)。  
  
## <a name="grouping-data-group-by"></a>对数据进行分组 （分组依据）  
 您可以添加`Group By`子句根据一个或多个字段的元素的查询结果中的元素进行分组。 例如，以下代码按类年分组学生。  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 如果运行此代码中使用的列表中创建的学生[如何：创建列表项](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)，从输出`For Each`语句是：  
  
 年份：初级  
  
 Tucker Michael  
  
 Garcia Hugo  
  
 Garcia Debra  
  
 Tucker Lance  
  
 年份：高级  
  
 Omelchenko, Svetlana  
  
 Osada Michiko  
  
 Fakhouri Fadi  
  
 汉英冯  
  
 Terry Adams  
  
 年份：新生  
  
 Mortensen, Sven  
  
 Garcia Cesar  
  
 以下代码所示的变体订单类年，而然后按姓氏排序每个年级学生。  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 有关详细信息`Group By`，请参阅[组 By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Collections.Generic.IEnumerable%601>
- [Visual Basic 中的 LINQ 入门](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [查询](../../../../visual-basic/language-reference/queries/index.md)
- [标准查询运算符概述 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
