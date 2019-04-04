---
title: 如何：修改表达式树 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: c53983c6dfc601a7e8e32ad020f5f7feb66cfe04
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834330"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>如何：修改表达式树 (Visual Basic)
本主题演示如何修改表达式树。 表达式树是不可变的，这意味着不能直接对它们进行修改。 若要更改表达式树，必须创建现有表达式树的副本，创建此副本后，进行必要的更改。 可以使用 <xref:System.Linq.Expressions.ExpressionVisitor> 类遍历现有表达式树，以及复制它访问的每个节点。  
  
### <a name="to-modify-an-expression-tree"></a>修改表达式树  
  
1.  创建新的**控制台应用程序**项目。  
  
2.  添加`Imports`语句的文件的`System.Linq.Expressions`命名空间。  
  
3.  向项目中添加 `AndAlsoModifier` 类。  
  
    ```vb  
    Public Class AndAlsoModifier  
        Inherits ExpressionVisitor  
  
        Public Function Modify(ByVal expr As Expression) As Expression  
            Return Visit(expr)  
        End Function  
  
        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression  
            If b.NodeType = ExpressionType.AndAlso Then  
                Dim left = Me.Visit(b.Left)  
                Dim right = Me.Visit(b.Right)  
  
                ' Make this binary expression an OrElse operation instead   
                ' of an AndAlso operation.  
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _  
                                             b.IsLiftedToNull, b.Method)  
            End If  
  
            Return MyBase.VisitBinary(b)  
        End Function  
    End Class  
    ```  
  
     此类继承 <xref:System.Linq.Expressions.ExpressionVisitor> 类，并且专用于修改表示条件 `AND` 运算的表达式。 它将运算从条件 `AND` 更改为条件 `OR`。 若要执行此操作，此类替代基类型的 <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> 方法，因为条件 `AND` 表达式表示为二进制表达式。 在 `VisitBinary` 方法中，如果传递给它的表达式表示条件 `AND` 操作，那么代码将构造一个新的表达式，此表达式包含条件 `OR` 运算符，而不是条件 `AND` 运算符。 如果传递给 `VisitBinary` 的表达式不表示条件 `AND` 运算，那么此方法遵从基类实现。 基类方法构造类似于所传递的表达式树的节点，但是这些节点将子树替换为访问者以递归方式生成的表达式树。  
  
4.  添加`Imports`语句的文件的`System.Linq.Expressions`命名空间。  
  
5.  将代码添加到`Main`Module1.vb 文件来创建表达式树，并将其传递给该方法的方法中需要修改它。  
  
    ```vb  
    Dim expr As Expression(Of Func(Of String, Boolean)) = _  
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")  
  
    Console.WriteLine(expr)  
  
    Dim modifier As New AndAlsoModifier()  
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))  
  
    Console.WriteLine(modifiedExpr)  
  
    ' This code produces the following output:  
    ' name => ((name.Length > 10) && name.StartsWith("G"))  
    ' name => ((name.Length > 10) || name.StartsWith("G"))  
    ```  
  
     此代码创建的表达式中包含条件 `AND` 运算。 然后，此代码创建 `AndAlsoModifier` 类的实例，并将表达式传递给此类的 `Modify` 方法。 输出原始以及修改后的表达式树以显示更改。  
  
6.  编译并运行该应用程序。  
  
## <a name="see-also"></a>请参阅

- [如何：执行表达式树 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [表达式树 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
