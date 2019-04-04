---
title: 字符数据类型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 14085172a8f9f9d60af0495a36dd4ba7592213fa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840973"
---
# <a name="character-data-types-visual-basic"></a>字符数据类型 (Visual Basic)
Visual Basic 提供了一些*字符数据类型*来处理可打印和可显示的字符。 尽管它们都处理 Unicode 字符`Char`包含一个字符，而`String`包含字符数量不确定。  
  
 显示的 Visual Basic 数据类型的并排比较的表，请参阅[数据类型](../../../../visual-basic/language-reference/data-types/index.md)。  
  
## <a name="char-type"></a>Char 类型  
 `Char`数据类型是一个单一的两个字节 （16 位） Unicode 字符。 如果某个变量始终存储的一个字符，将其声明为`Char`。 例如：  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 在每个可能值`Char`或`String`变量是*代码点*，或在 Unicode 字符集中的字符代码。 Unicode 字符包含基本 ASCII 字符集、 各种其他字母、 重音符号、 货币符号、 分数、 音调符号和数学和技术符号。  
  
> [!NOTE]
>  Unicode 字符设置的码位 D800 到 DFFF (十进制是从 55296 到 55551) 为预留*代理项对*，这需要两个 16 位值表示一个码位。 一个`Char`变量不能包含代理项对和一个`String`使用两个位置来保存此类对。  
  
 有关详细信息，请参阅[Char 数据类型](../../../../visual-basic/language-reference/data-types/char-data-type.md)。  
  
## <a name="string-type"></a>字符串类型  
 `String`数据类型是零个或多个双字节 （16 位） Unicode 字符序列。 如果一个变量可以包含字符数量不确定，其声明为`String`。 例如：  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 有关详细信息，请参阅[字符串数据类型](../../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
## <a name="see-also"></a>请参阅

- [基本数据类型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [复合数据类型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Visual Basic 中的泛型类型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [在 Visual Basic 中的类型转换](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [数据类型疑难解答](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [类型字符](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
