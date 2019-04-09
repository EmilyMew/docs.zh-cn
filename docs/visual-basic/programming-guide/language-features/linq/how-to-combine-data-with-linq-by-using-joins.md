---
title: 如何：通过合并数据 LINQ 使用联接 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: dde627edfeb1d4473c9d2e01b9ff83c580a0f122
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822682"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>如何：通过合并数据 LINQ 使用联接 (Visual Basic)
Visual Basic 提供了一些`Join`和`Group Join`查询子句以使您能够合并多个集合根据集合之间的常见值的内容。 这些值称为*密钥*值。 开发人员熟悉关系数据库的概念将识别`Join`INNER JOIN 子句和`Group Join`作为，实际上，左外部联接子句。  
  
 本主题中的示例演示了几种方法使用合并数据`Join`和`Group Join`查询子句。  
  
## <a name="create-a-project-and-add-sample-data"></a>创建项目并添加示例数据  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>若要创建包含示例数据和类型的项目  
  
1.  若要运行本主题中的示例，请打开 Visual Studio，并添加新的 Visual Basic 控制台应用程序项目。 双击创建 Visual Basic 的 Module1.vb 文件。  
  
2.  在本主题使用示例`Person`和`Pet`类型和数据从下面的代码示例。 将此代码复制到默认`Module1`创建 Visual Basic 模块。  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>通过使用联接子句执行内部联接  
 INNER JOIN 结合了两个集合中的数据。 包含为其指定的密钥值匹配的项。 不是集合中的另一个集合中没有匹配项的项。  
  
 在 Visual Basic 中，LINQ 提供了用于执行内部联接的两个选项： 隐式联接和显式联接。  
  
 隐式联接指定集合要联接`From`子句，并标识中匹配的键字段`Where`子句。 Visual Basic 隐式联接两个集合根据指定的键字段。  
  
 可以通过使用指定的显式联接`Join`子句时想可以细致地指出哪个密钥在联接中使用的字段。 在这种情况下，`Where`子句仍可用于筛选查询结果。  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>若要执行 Inner Join 使用 Join 子句  
  
1.  将以下代码添加到`Module1`项目若要查看这两个隐式和显式内部联接的示例中的模块。  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>使用 Group Join 子句执行左外部联接  
 LEFT OUTER JOIN 包括所有的项从左侧集合联接和仅匹配联接的右端集合中的值。 从右侧集合联接的左侧集合中没有匹配项的任何项不在查询结果。  
  
 `Group Join`子句执行时，实际上，左外部联接。 通常称作 LEFT OUTER JOIN 和之间的区别`Group Join`子句将返回在于`Group Join`子句从左侧集合中每一项联接右侧集合对结果进行分组。 在关系数据库中，左外部联接返回在其在查询中的每个项生成一个未分组的结果包含联接这两个集合中的匹配项。 在这种情况下，从左侧集合联接的项的右侧集合的每个匹配项都重复。 您将看到这种情况下一个过程完成。  
  
 你可以检索的结果`Group Join`查询与通过扩展查询，以返回每个分组的查询结果的项分组结果的查询。 若要实现此目的，必须确保您查询在`DefaultIfEmpty`分组集合的方法。 这可确保，联接的左侧集合中的项仍包含在查询结果即使它们具有匹配的结果从右侧的集合。 可以将代码添加到查询以从联接的右侧集合没有匹配值时提供一个默认结果值。  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>若要通过使用 Group Join 子句执行左外部联接  
  
1.  将以下代码添加到`Module1`项目以查看分组左外部联接和分组的左外部联接的示例中的模块。  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>使用组合键进行联接  
 可以使用`And`中的关键字`Join`或`Group Join`子句来标识匹配时要使用的多个键字段值从要联接的集合。 `And`关键字指定所有指定的键字段都必须匹配要联接的项。  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>使用组合键进行联接  
  
1.  将以下代码添加到`Module1`项目若要查看使用复合键联接的示例中的模块。  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>运行代码  
  
#### <a name="to-add-code-to-run-the-examples"></a>若要添加代码以运行示例  
  
1.  替换`Sub Main`在`Module1`以下代码，以运行本主题中的示例项目中的模块。  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2.  按 F5 以运行示例。  
  
## <a name="see-also"></a>请参阅

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Join 子句](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join 子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)
- [查询](../../../../visual-basic/language-reference/queries/index.md)
- [使用 LINQ 进行数据转换 (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
