---
title: Enum 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: fa97a374d4570e014222bf44844271b3394453da
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830066"
---
# <a name="enum-statement-visual-basic"></a>Enum 语句 (Visual Basic)
声明枚举并定义其成员的值。  
  
## <a name="syntax"></a>语法  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a>部件  
  
-   `attributelist`  
  
     可选。 应用于此枚举的属性列表。 必须将[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)括进尖括号 ("`<`"和"`>`")。  
  
     <xref:System.FlagsAttribute>特性指示实例的枚举值可以包含多个枚举成员，并且每个成员表示的枚举值中的位字段。  
  
-   `accessmodifier`  
  
     可选。 指定哪些代码可以访问此枚举。 可以是以下各项之一：  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Protected Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Private Protected](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     可选。 指定此枚举重新声明并隐藏具有相同名称的编程元素或在基类中的重载元素集。 您可以指定[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)不上的任何成员，而仅在该枚举本身上。  
  
-   `enumerationname`  
  
     必需。 枚举的名称。 有关有效的名称的信息，请参阅[声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   `datatype`  
  
     可选。 枚举及其所有成员的数据类型。  
  
-   `memberlist`  
  
     必需。 此语句中声明的成员常量的列表。 在各个源代码行上显示多个成员。  
  
     每个`member`具有以下语法和部分： `[<attribute list>] member name [ = initializer ]`  
  
    |部件|描述|  
    |---|---|  
    |`membername`|必需。 此成员的名称。|  
    |`initializer`|可选。 在编译时计算和分配给此成员的表达式。|  
  
-   `End` `Enum`  
  
     终止 `Enum` 块。  
  
## <a name="remarks"></a>备注  
 如果有一组逻辑上彼此相关的不变值，您可以在枚举中一起定义它们。 这提供了枚举和其成员，其值比更容易记忆有意义的名称。 然后可以在代码中，在多个位置中使用的枚举成员。  
  
 使用枚举的好处包括：  
  
-   这样可以减少错误引起的转置或键入数字。  
  
-   便于将来更改值。  
  
-   使代码易于阅读，这意味着它不太可能将引入错误。  
  
-   可确保向前兼容性。 如果使用枚举，您的代码是不太可能会失败，如果有人在将来更改的成员名称与对应的值。  
  
 枚举具有名称、 基础数据类型和一组的成员。 每个成员都表示一个常数。  
  
 在类、 结构、 模块或接口级别，在任何过程中，外部声明的枚举是*成员枚举*。 它是类、 结构、 模块或接口声明它的成员。  
  
 成员枚举可以是从任何位置访问其类、 结构、 模块或接口。 代码类之外，结构或模块必须限定成员枚举的名称，并且该类、 结构或模块的名称。 你可以无需通过添加使用完全限定的名称[导入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)语句的源文件。  
  
 在命名空间级别，任何类、 结构、 模块或接口，外部声明的枚举是它所在的命名空间的成员。  
  
 *声明上下文*枚举必须是源文件、 命名空间、 类、 结构、 模块或接口，并且不能为一个过程。 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 您可以将特性应用到枚举作为一个整体，而不是属于其成员分别。 属性提供对程序集的元数据的信息。  
  
## <a name="data-type"></a>数据类型  
 `Enum`语句可以声明枚举的数据类型。 每个成员将在枚举的数据类型。 您可以指定`Byte`， `Integer`， `Long`， `SByte`， `Short`， `UInteger`， `ULong`，或`UShort`。  
  
 如果未指定`datatype`枚举中，对于每个成员采用的数据类型及其`initializer`。 如果同时指定`datatype`并`initializer`的数据类型`initializer`必须可转换为`datatype`。 如果既没有`datatype`也不`initializer`存在，则数据类型默认为`Integer`。  
  
## <a name="initializing-members"></a>初始化成员  
 `Enum`语句可以初始化中的所选成员的内容`memberlist`。 您使用`initializer`提供要分配给成员的表达式。  
  
 如果未指定`initializer`成员，Visual Basic 将它初始化为零 (如果它是第一个`member`中`memberlist`)，或为值比前面紧邻的大 1 `member`。  
  
 在每个提供的表达式`initializer`可以是文本、 其他常量已定义的和已定义，包括以前的此枚举成员的枚举成员的任意组合。 可以使用算术和逻辑运算符来组合这些元素。  
  
 不能使用变量或函数中的`initializer`。 但是，可以使用转换关键字如`CByte`和`CShort`。 此外可以使用`AscW`如果调用与常量`String`或`Char`参数，因为可以在编译时计算。  
  
 枚举不能具有浮点值。 如果将成员分配一个浮点值和`Option Strict`设置为 on，会发生编译器错误。 如果`Option Strict`处于关闭状态，值自动转换为`Enum`类型。  
  
 如果某个成员的值超出了允许的范围的基础数据类型，或者如果初始化任何成员添加到基础数据类型所允许的最大值，编译器会报告错误。  
  
## <a name="modifiers"></a>修饰符  
 类、 结构、 模块和接口成员枚举默认为公共访问权限。 您可以调整其访问级别和访问修饰符。 Namespace 成员枚举默认为友元访问权限。 您可以调整其公共的但无法访问私有或受保护的访问级别。 有关详细信息，请参阅[访问 Visual Basic 中的级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 所有枚举成员都具有公共访问权限，并且不能对其使用任何访问修饰符。 但是，如果该枚举本身的更受限制的访问级别，指定的枚举的访问级别优先。  
  
 默认情况下，所有枚举都是类型，其字段都是常量。 因此`Shared`， `Static`，和`ReadOnly`声明枚举或其成员时，不能使用关键字。  
  
## <a name="assigning-multiple-values"></a>分配多个值  
 枚举通常表示互斥的值。 通过包括<xref:System.FlagsAttribute>属性中`Enum`声明中，您可以改为分配多个值的枚举的实例。 <xref:System.FlagsAttribute>属性指定枚举视为位字段，即一组标志。 这些被称为*按位*枚举。  
  
 当使用声明枚举<xref:System.FlagsAttribute>属性中，我们建议使用的是 2、 1、 2、 4、 8、 16 和等等，幂的值。 我们还建议"None"是其值为 0 的成员的名称。 有关其他指南，请参阅<xref:System.FlagsAttribute>和<xref:System.Enum>。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 `Enum` 语句。 请注意，该成员被称为`EggSizeEnum.Medium`，而不是作为`Medium`。  
  
 [!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]  
  
## <a name="example"></a>示例  
 下面的示例中的方法是外部`Egg`类。 因此，`EggSizeEnum`完全限定为`Egg.EggSizeEnum`。  
  
 [!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]  
  
## <a name="example"></a>示例  
 下面的示例使用`Enum`语句来定义一组相关的命名常量的值。 在这种情况下，值是您可能选择设计为数据库的数据输入窗体的颜色。  
  
 [!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]  
  
## <a name="example"></a>示例  
 下面的示例显示了包括正和负号的值。  
  
 [!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]  
  
## <a name="example"></a>示例  
 在以下示例中，`As`子句用于指定`datatype`的枚举。  
  
 [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用按位枚举。 多个值可以分配给的按位枚举的实例。 `Enum`声明包括<xref:System.FlagsAttribute>属性，指示可以将枚举视为一组标志。  
  
 [!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]  
  
## <a name="example"></a>示例  
 下面的示例循环访问枚举。 它使用<xref:System.Enum.GetNames%2A>方法从枚举检索的成员名称的数组和<xref:System.Enum.GetValues%2A>检索成员值的数组。  
  
 [!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const 语句](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)
- [隐式转换和显式转换](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [常量和枚举](../../../visual-basic/language-reference/constants-and-enumerations.md)
