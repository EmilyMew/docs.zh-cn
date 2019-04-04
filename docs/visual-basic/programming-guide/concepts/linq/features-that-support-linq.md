---
title: 支持 LINQ 的 Visual Basic 功能
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 155d5c36483accc12d066a5530fea20a563e1498
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814492"
---
# <a name="visual-basic-features-that-support-linq"></a>支持 LINQ 的 Visual Basic 功能
名称[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]指的是在 Visual Basic 支持查询语法和其他语言构造大大降低直接在语言中的技术。 使用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，无需学习新语言对外部数据源的查询。 可以通过使用 Visual Basic 针对关系数据库、 XML 存储或对象中的数据进行查询。 此集成的语言的查询功能，编译时检查语法错误和类型安全。 这种集成还可确保您已知道大多数您需要了解在 Visual Basic 中编写丰富而各不相同的查询。  
  
 以下部分介绍在足够的详细信息，以便可以开始阅读介绍性文档、 代码示例和示例应用程序中支持 LINQ 的语言构造。 您还可以单击链接，以了解如何语言功能组合在一起以实现语言集成查询的更详细的解释。 启动的好时机是[演练：在 Visual Basic 中编写查询](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)。  
  
## <a name="query-expressions"></a>查询表达式  
 在 Visual Basic 中的查询表达式可以用类似于 SQL 或 XQuery 的声明性语法来表示。 在编译时，查询语法转换为对标准查询运算符扩展方法的 LINQ 提供程序实现的方法调用。 应用程序控制的标准查询运算符是在范围内通过指定适当的命名空间与`Imports`语句。 Visual Basic 查询表达式的语法如下所示：  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 有关详细信息，请参阅[Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
## <a name="implicitly-typed-variables"></a>隐式类型化的变量  
 而不是显式指定类型声明和初始化一个变量时，可以使编译器能够推断和分配类型。 这被称为*局部类型推理*。  
  
 变量推断其类型强类型，就像您显式指定其类型的变量一样。 局部类型推理仅适用于定义方法体内局部变量。 有关详细信息，请参阅[Option Infer 语句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)并[本地类型推断](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
 下面的示例说明了局部类型推理。 若要使用此示例中，必须设置`Option Infer`到`On`。  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 局部类型推理还，可以创建匿名类型，也不能在本部分稍后介绍 LINQ 查询所必需的。  
  
 在下面的 LINQ 示例中，类型推理发生如果`Option Infer`可以是`On`或`Off`。 如果会发生编译时错误`Option Infer`是`Off`并`Option Strict`是`On`。  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a>对象初始值设定项  
 您必须创建匿名类型来存储查询的结果时，将在查询表达式中使用对象初始值设定项。 它们还可用于初始化外部查询的命名类型的对象。 通过使用对象初始值设定项，可以无需显式调用构造函数初始化单个行中的对象。 假设你有一个名为类`Customer`具有公共`Name`和`Phone`属性，以及其他属性，可以以这种方式使用对象初始值设定项：  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 有关详细信息，请参阅[对象初始值设定项：命名和匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。  
  
## <a name="anonymous-types"></a>匿名类型  
 匿名类型提供的一组属性临时分组你想要在查询结果中包含的元素的简便方法。 这使您可以在查询中，按任意顺序中，选择可用字段的任意组合，而无需定义元素的已命名的数据类型。  
  
 *匿名类型*编译器动态构造。 类型的名称分配由编译器，并且它可能会更改与每个新的编译。 因此，不能直接使用该名称。 按以下方式初始化匿名类型：  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 有关详细信息，请参阅[匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## <a name="extension-methods"></a>扩展方法  
 扩展方法，可将方法添加到数据类型或接口定义之外的位置。 此功能可以以，实际上，向现有类型添加新方法，而无需实际修改类型。 标准查询运算符本身就是一组提供的扩展方法[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查询功能实现的任何类型<xref:System.Collections.Generic.IEnumerable%601>。 其他扩展<xref:System.Collections.Generic.IEnumerable%601>包括<xref:System.Linq.Enumerable.Count%2A>， <xref:System.Linq.Enumerable.Union%2A>，和<xref:System.Linq.Enumerable.Intersect%2A>。  
  
 以下扩展方法将添加到了 print 方法<xref:System.String>类。  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 类似于普通实例方法的调用的方法<xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 有关详细信息，请参阅[扩展方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。  
  
## <a name="lambda-expressions"></a>Lambda 表达式  
 Lambda 表达式是没有名称，用于计算并返回单个值的函数。 命名与函数不同，可以定义并在同一时间执行 lambda 表达式。 以下示例显示 4。  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 您可以将 lambda 表达式定义分配给变量的名称，然后使用名称来调用该函数。 下面的示例还显示 4。  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 在[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，lambda 表达式基础许多标准查询运算符。 编译器会创建 lambda 表达式，以捕获等基本查询方法中定义的计算`Where`， `Select`， `Order By`， `Take While`，等等。  
  
 例如，以下代码定义学生列表中返回所有高年级学生的查询。  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 查询定义编译为类似于下面的示例使用两个 lambda 表达式来指定的参数的代码`Where`和`Select`。  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 可以使用运行任一版本`For Each`循环：  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 有关详细信息，请参阅 [Lambda 表达式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
## <a name="see-also"></a>请参阅

- [语言集成查询 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Visual Basic 中的 LINQ 入门](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [LINQ 和字符串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [Option Infer 语句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
