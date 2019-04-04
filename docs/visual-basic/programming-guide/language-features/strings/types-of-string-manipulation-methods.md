---
title: 字符串操作方法的类型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 44eb101ebdfeb316958a659107190ef1fc84df44
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821148"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>字符串操作方法的类型 (Visual Basic)
有几种不同的方法来分析和操作字符串。 某些方法是 Visual Basic 语言的一部分，而有些固有`String`类。  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic 语言和.NET Framework  
 Visual Basic 方法用作语言的固有功能。 他们可能使用而无需在代码中的限定。 下面的示例演示 Visual Basic 字符串操作命令的典型用法：  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 在此示例中，`Mid`函数对执行直接运算`aString`并将值分配给`bString`。  
  
 Visual Basic 字符串操作方法的列表，请参阅[字符串操作摘要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)。  
  
### <a name="shared-methods-and-instance-methods"></a>共享的方法和实例方法  
 您还可以使用方法的操作字符串`String`类。 有两种类型的方法中`String`:*共享*方法并*实例*方法。  
  
#### <a name="shared-methods"></a>共享的方法  
 共享的方法是源于方法`String`类本身并不需要处理，该类的实例。 这些方法可使用的类名称限定 (`String`)，而非包含的实例`String`类。 例如：  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 在前面的示例中，<xref:System.String.Copy%2A?displayProperty=nameWithType>方法是静态方法，对表达式的行为它给出并将结果值输出到`bString`。  
  
#### <a name="instance-methods"></a>实例方法  
 实例方法，与此相反，源于的特定实例`String`，并且必须具有实例名称限定。 例如：  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 在此示例中，<xref:System.String.Substring%2A?displayProperty=nameWithType>方法是一种方法的实例的`String`(即， `aString`)。 它对执行操作`aString`并将该值赋予`bString`。  
  
 有关详细信息，请参阅的文档<xref:System.String>类。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的字符串简介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
