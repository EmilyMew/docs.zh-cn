---
title: 如何：控制变量 (Visual Basic 中) 的可用性
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: fb7c04ac6c24648dfb2a8cfa5e01bf97c6b0b3be
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841688"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>如何：控制变量 (Visual Basic 中) 的可用性
通过指定控制变量的可用性及其*访问级别*。 访问级别确定哪些代码有权读取或写入到该变量。  
  
-   *成员变量*（定义在模块级别和任何过程之外） 默认为公共访问，这意味着用户可以看见任何代码可以访问它们。 可以通过指定访问修饰符对此进行更改。  
  
-   *本地变量*（定义在过程内） 名义上具有公共访问，虽然只有其过程中的代码可以访问它们。 不能更改访问级别的本地变量，但可以更改包含它的过程的访问级别。  
  
 有关详细信息，请参阅[访问 Visual Basic 中的级别](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="private-and-public-access"></a>专用和公共访问  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>若要使变量只能在其模块、 类或结构内访问  
  
1.  位置[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)内部模块、 类或结构，但在任何过程外部的变量。  
  
2.  包括[私有](../../../../visual-basic/language-reference/modifiers/private.md)中的关键字`Dim`语句。  
  
     可以读取或写入到中的变量中的模块、 类或结构的任意位置，但不能从其外部。  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>若要使变量可从任何可以看到它的代码访问  
  
1.  成员变量，将放置`Dim`内部模块、 类或结构，但在任何过程外部变量的语句。  
  
2.  包括[公共](../../../../visual-basic/language-reference/modifiers/public.md)中的关键字`Dim`语句。  
  
     可读取或从任何互操作的代码与您的程序集写入变量。  
  
 或  
  
1.  本地变量，将放置`Dim`过程内的变量的语句。  
  
2.  不包括`Public`中的关键字`Dim`语句。  
  
     你可以读取或写入过程中的任意位置，但不能从变量到其外部。  
  
## <a name="protected-and-friend-access"></a>受保护和友元访问权限  
 您可以限制到其类和任何派生的类，或它的程序集的变量的访问级别。 此外可以指定这些限制，可从代码访问权限，任何派生类中或在同一程序集中的任何其他位置中的并集。 通过组合指定了此 union`Protected`和`Friend`同一声明中的关键字。  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>若要使变量只能从其类和任何派生的类中访问  
  
1.  位置`Dim`类的内部，但在任何过程外部变量的语句。  
  
2.  包括[受保护](../../../../visual-basic/language-reference/modifiers/protected.md)中的关键字`Dim`语句。  
  
     可读取或写入任意位置在类中，以及从变量的任何类派生，但不能从任何类进行派生链中的外部。  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>若要使变量只能在同一程序集内访问  
  
1.  位置`Dim`内部模块、 类或结构，但在任何过程外部变量的语句。  
  
2.  包括[友元](../../../../visual-basic/language-reference/modifiers/friend.md)中的关键字`Dim`语句。  
  
     可读取或写入模块、 类或结构中的任意位置以及从同一程序集中，但不能从任何代码从变量到程序集之外。  
  
## <a name="example"></a>示例  
 下面的示例演示使用的变量的声明`Public`， `Protected`， `Friend`， `Protected Friend`，和`Private`访问级别。 请注意，当`Dim`语句指定访问级别时，不需要包括`Dim`关键字。  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 限制性更强的变量的访问级别，使用它的变量越小恶意代码可以进行不正确的机会。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中的访问级别](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../../visual-basic/language-reference/modifiers/private.md)
