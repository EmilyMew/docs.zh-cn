---
title: 如何：在 Visual Basic 中使用 StringBuilder 创建字符串
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 00fefcc138164288d872cd339f165dc6ffc0131a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834187"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>如何：在 Visual Basic 中使用 StringBuilder 创建字符串
以下示例构造一个长字符串从使用许多较小字符串<xref:System.Text.StringBuilder>类。 <xref:System.Text.StringBuilder>类是比效率更高`&=`将许多字符串连接运算符。  
  
## <a name="example"></a>示例  
 下面的示例创建的实例<xref:System.Text.StringBuilder>类，将 1,000 字符串追加到该实例，然后返回该字符串表示形式。  
  
 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]  
  
## <a name="see-also"></a>请参阅

- [使用 StringBuilder 类](../../../../standard/base-types/stringbuilder.md)
- [&= 运算符](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [字符串](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [新建字符串](../../../../standard/base-types/creating-new.md)
- [控制字符串](../../../../standard/base-types/manipulating-strings.md)
