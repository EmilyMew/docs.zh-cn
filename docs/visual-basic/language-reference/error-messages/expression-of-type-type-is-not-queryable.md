---
title: 类型 <type> 的表达式不可查询
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 7f74d56b47629ff76f9b935d26278ace8df4c353
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842325"
---
# <a name="expression-of-type-type-is-not-queryable"></a>类型的表达式\<类型 > 不可查询
类型的表达式\<类型 > 不可查询。 请确保不缺少程序集引用和/或命名空间导入 LINQ 提供程序。  
  
 可查询类型中定义<xref:System.Linq>， <xref:System.Data.Linq>，和<xref:System.Xml.Linq>命名空间。 必须导入一个或多个这些命名空间执行 LINQ 查询。  
  
 <xref:System.Linq>命名空间能让您对查询对象，如集合和数组使用 LINQ。  
  
 <xref:System.Data.Linq>命名空间，可使用 LINQ 查询 ADO.NET 数据集和 SQL Server 数据库。  
  
 <xref:System.Xml.Linq>命名空间用于查询 XML 使用 LINQ 和 Visual Basic 中使用 XML 功能。  
  
 **错误 ID:** BC36593  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  添加`Import`语句<xref:System.Linq>， <xref:System.Data.Linq>，或<xref:System.Xml.Linq>到你的代码文件的命名空间。 您可以还使用导入命名空间为你的项目**引用**的项目设计器页 (**我的项目**)。  
  
2.  请确保已标识为您的查询的源是可查询类型的类型。 也就是说，实现的类型<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
- [引用和 Imports 语句](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports 语句（.NET 命名空间和类型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [项目设计器 ->“引用”页 (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
