---
title: Delegate 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 880b4cf75d518506d2bcf788ad8460274dcccefc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821304"
---
# <a name="delegate-statement"></a>Delegate 语句
用于声明委托。 委托是一个引用类型，是指`Shared`方法的类型或实例方法的对象。 任何具有匹配的参数和返回类型的过程可以用于创建此委托类的实例。 然后可以通过委托实例更高版本调用该过程。  
  
## <a name="syntax"></a>语法  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`attrlist`|可选。 将应用于此委托的特性的列表。 用逗号分隔多个属性。 必须将[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)括进尖括号 ("`<`"和"`>`")。|  
|`accessmodifier`|可选。 指定哪些代码可以访问该委托。 可以是以下各项之一：<br /><br /> - [公共](../../../visual-basic/language-reference/modifiers/public.md)。 可以访问的元素声明委托的任何代码都可以访问它。<br />-   [受保护的](../../../visual-basic/language-reference/modifiers/protected.md)。 只有在委托的类或派生的类中的代码可以访问它。<br />-   [友元](../../../visual-basic/language-reference/modifiers/friend.md)。 只有在同一程序集中的代码可以访问该委托。<br />- [专用](../../../visual-basic/language-reference/modifiers/private.md)。 只有声明委托的元素内的代码可以访问它。<br /><br /> - [受保护的友元](../../language-reference/modifiers/protected-friend.md)只有在委托的类，派生的类中或在同一程序集中的代码才能访问该委托。 <br />- [专用受保护](../../language-reference/modifiers/private-protected.md)只有委托的类或通过在同一程序集中的派生类中的代码可以访问该委托。 |  
|`Shadows`|可选。 指示此委托重新声明并隐藏具有相同名称的编程元素或在基类中的重载元素集。 可以与任何其他类型一起隐藏任何类型的已声明元素。<br /><br /> 隐藏的元素不可在隐藏它的派生类中使用（除了从隐藏元素不可访问的位置）。 例如，如果`Private`元素将隐藏基类元素，不具有访问权限的代码`Private`元素将改为访问的基类元素。|  
|`Sub`|（可选），但`Sub`或`Function`必须出现。 将委托作为此过程声明`Sub`不返回值的过程。|  
|`Function`|（可选），但`Sub`或`Function`必须出现。 将委托作为此过程声明`Function`返回一个值的过程。|  
|`name`|必需。 委托类型; 的名称遵循标准变量命名约定。|  
|`typeparamlist`|可选。 此委托的类型参数列表。 由逗号分隔多个类型参数。 （可选） 每个类型参数可以声明变体使用`In`和`Out`泛型修饰符。 必须将[类型列表](../../../visual-basic/language-reference/statements/type-list.md)在括号中，并引入其与`Of`关键字。|  
|`parameterlist`|可选。 被调用时传递给过程的参数的列表。 必须将[参数列表](../../../visual-basic/language-reference/statements/parameter-list.md)在括号中。|  
|`type`|如果指定，则必需`Function`过程。 返回值的数据类型。|  
  
## <a name="remarks"></a>备注  
 `Delegate`语句定义委托类的参数和返回类型。 任何具有匹配的参数和返回类型的过程可以用于创建此委托类的实例。 然后就可以将调用过程通过委托实例中，通过调用委托的`Invoke`方法。  
  
 可以在命名空间、 模块、 类或结构级别，但不是能在过程声明委托。  
  
 每个委托类均可定义将对象方法指定传递到的构造函数。 委托构造函数的自变量必须是对方法的引用或 lambda 表达式。  
  
 若要指定对方法的引用，请使用以下语法：  
  
 `AddressOf` [`expression`.]`methodname`  
  
 `expression` 的编译时类型必须是类或接口的名称，此类或接口包含指定名称的方法，其签名与委托类的签名一致。 `methodname` 可以是共享方法，也可以是实例方法。 即使为类的默认方法创建委托，`methodname` 也不是可选的。  
  
 若要指定 lambda 表达式，请使用以下语法：  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 函数的签名必须与委托类型的签名一致。 有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 有关委托的详细信息，请参阅[委托](../../../visual-basic/programming-guide/language-features/delegates/index.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`Delegate`语句声明委托对两个数字进行运算并返回一个数字。 `DelegateTest`方法采用这种类型的委托的实例并使用它来对的编号对。  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>请参阅

- [AddressOf 运算符](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Of](../../../visual-basic/language-reference/statements/of-clause.md)
- [委托](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [如何：使用泛型类](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Visual Basic 中的泛型类型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [协变和逆变](../../programming-guide/concepts/covariance-contravariance/index.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
