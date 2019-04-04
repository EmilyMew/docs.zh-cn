---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 98dafab3e524ea371bba228eb231e28d46cc3b4e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819445"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
指定 Visual Basic 应封送到美国国家标准协会 (ANSI) 值，而不考虑所声明的外部过程的名称的所有字符串。  
  
 当调用在项目外部定义的过程时，Visual Basic 编译器没有访问正确调用该过程所需的信息。 此信息包括该过程所在的位置、 如何标识、 其调用的序列和返回类型和字符串字符将其设置使用。 [Declare 语句](../../../visual-basic/language-reference/statements/declare-statement.md)创建对外部过程的引用，并提供这些必需的信息。  
  
 `charsetmodifier`部分中`Declare`语句提供了有关期间对外部过程的调用封送处理字符串的字符组信息。 它还会影响 Visual Basic 如何搜索外部过程的名称的外部文件。 `Ansi`修饰符指定 Visual Basic 应封送为 ANSI 值的所有字符串，并应查找而无需在搜索过程中修改其名称的过程。  
  
 如果指定没有字符集修饰符，则`Ansi`是默认值。  
  
## <a name="remarks"></a>备注  
 `Ansi`修饰符可用于在此上下文中：  
  
 [Declare 语句](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>智能设备开发人员说明  
 不支持此关键字。  
  
## <a name="see-also"></a>请参阅

- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
