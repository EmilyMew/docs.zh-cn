---
title: Inherits 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 5ab90e44e2809c1e71d7f100970b7be73af4a732
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817092"
---
# <a name="inherits-statement"></a>Inherits Statement
导致当前类或接口继承另一个类或接口集的属性、 变量、 属性、 过程和事件。  
  
## <a name="syntax"></a>语法  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`basetypenames`|必需。 此类派生的类的名称。<br /><br /> 或<br /><br /> 此接口派生的接口的名称。 使用逗号分隔多个名称。|  
  
## <a name="remarks"></a>备注  
 如果使用，`Inherits`语句必须是类或接口定义中的第一个非空、 非注释行。 它应紧接`Class`或`Interface`语句。  
  
 可以使用`Inherits`只能在类或接口中。 这意味着继承的声明上下文不能是源文件、 命名空间、 结构、 模块、 过程或块。  
  
## <a name="rules"></a>规则  
  
-   **类继承。** 如果类使用`Inherits`语句中，可以指定只有一个基类。  
  
     类不能从嵌套在它的类继承。  
  
-   **接口继承。** 如果接口使用`Inherits`语句，则可以指定一个或多个基接口。 您可以即使它们每个定义具有相同名称的成员，从两个接口继承。 如果这样做，实现代码必须使用名称限定来指定它正在实现的成员。  
  
     接口不能从具有限制性更强的访问级别的另一个接口继承。 例如，`Public`不能继承自接口`Friend`接口。  
  
     接口不能从嵌套在它的接口继承。  
  
 .NET Framework 中的类继承的一个示例是<xref:System.ArgumentException>类，该类继承自<xref:System.SystemException>类。 这提供了到<xref:System.ArgumentException>所有预定义的属性和所需的系统异常，如过程<xref:System.Exception.Message%2A>属性和<xref:System.Exception.ToString%2A>方法。  
  
 .NET Framework 中的接口继承的一个示例是<xref:System.Collections.ICollection>接口，该类继承自<xref:System.Collections.IEnumerable>接口。 这将导致<xref:System.Collections.ICollection>继承需要遍历集合的枚举器的定义。  
  
## <a name="example"></a>示例  
 下面的示例使用`Inherits`语句，以显示一个类的名为`thisClass`可继承的名为的基类的所有成员`anotherClass`。  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>示例  
 下面的示例显示了多个接口继承。  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 名为的接口`thisInterface`现在包括中的所有定义<xref:System.IComparable>， <xref:System.IDisposable>，和<xref:System.IFormattable>接口继承的成员分别提供有关特定于类型的比较的两个对象，释放分配的资源表示为对象的值和`String`。 实现的类`thisInterface`必须实现每个基接口的每个成员。  
  
## <a name="see-also"></a>请参阅

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [继承的基础知识](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [接口](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
