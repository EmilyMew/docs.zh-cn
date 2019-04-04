---
title: 继承的基础知识 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 5e4b8511145e758bf3d6328141be0e526965dccf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826569"
---
# <a name="inheritance-basics-visual-basic"></a>继承的基础知识 (Visual Basic)
`Inherits`语句用于声明一个名为的新类*派生类*基于现有类，称为*基类*。 派生的类继承，并可以扩展属性、 方法、 事件、 字段和基类中定义的常量。 以下部分介绍了一些有关继承的规则和修饰符可用于更改方式类继承，或将继承：  
  
-   默认情况下，所有类都是可继承的除非标记为`NotInheritable`关键字。 从你的项目中的其他类或在你的项目引用其他程序集中的类，类可以继承。  
  
-   与允许多个继承的语言，Visual Basic 只允许单个继承类; 中也就是说，派生的类可以有一个基类。 虽然类中不允许多个继承，类可以实现多个接口，这样可以有效地实现相同目的。  
  
-   若要防止公开限制在基类中的项，必须等于或高于其基本类派生的类的访问类型。 例如，`Public`类不能继承`Friend`或`Private`类，和一个`Friend`类不能继承`Private`类。  
  
## <a name="inheritance-modifiers"></a>继承修饰符  
 以下类级语句和修饰符以支持继承，引入了 Visual Basic:  
  
-   `Inherits` 语句-指定的基类。  
  
-   `NotInheritable` 修饰符，使程序员使用类作为基类。  
  
-   `MustInherit` 修饰符-指定类旨在用作仅基类。 实例`MustInherit`类不能直接创建; 他们只能在创建的派生类作为基类的类实例。 (其他编程语言，如 c + + 和C#，使用术语*抽象类*来描述此类的类。)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>属性和方法在派生类中的重写  
 默认情况下，派生的类从其基类中继承属性和方法。 如果继承的属性或方法的行为必须以不同的方式在派生类中它可以是*重写*。 也就是说，您可以在派生类中定义方法的新实现。 下列修饰符用于控制如何重写属性和方法：  
  
-   `Overridable` -允许的属性或方法中的类在派生类中重写。  
  
-   `Overrides` -重写`Overridable`属性或方法的基类中定义。  
  
-   `NotOverridable` -防止属性或方法被重写继承的类中。 默认情况下`Public`方法都是`NotOverridable`。  
  
-   `MustOverride` -需要在派生的类重写属性或方法。 当`MustOverride`使用关键字、 方法定义组成只`Sub`， `Function`，或`Property`语句。 不允许任何其他语句，以及具体而言是没有`End Sub`或`End Function`语句。 `MustOverride` 方法必须声明为中`MustInherit`类。  
  
 假设你想要定义要处理工资单类。 可以定义一个泛型`Payroll`类，该类包含`RunPayroll`典型周计算工资单的方法。 然后，可以使用`Payroll`用作基类的更专业`BonusPayroll`类，该类可以分发雇员奖金时使用。  
  
 `BonusPayroll`类可以继承，并且重写，请`PayEmployee`基类中定义的方法`Payroll`类。  
  
 下面的示例定义一个基类，`Payroll,`和派生的类`BonusPayroll`，这会重写继承的方法， `PayEmployee`。 一个过程中， `RunPayroll`，创建并随后将传递`Payroll`对象和一个`BonusPayroll`的函数对象`Pay`，用于执行`PayEmployee`这两个对象的方法。  
  
 [!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]  
  
## <a name="the-mybase-keyword"></a>MyBase 关键字  
 `MyBase`关键字的行为类似于一个类的当前实例的基类是指的对象变量。 `MyBase` 通常用于访问基类成员被重写或派生类中被隐藏。 具体而言，`MyBase.New`用于从派生的类构造函数中显式调用基类构造函数。  
  
 例如，假设您要设计一个重写从基类继承的方法的派生的类。 重写的方法可以调用基类中的方法，并修改返回的值，如下面的代码段中所示：  
  
 [!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]  
  
 以下列表描述对使用的限制`MyBase`:  
  
-   `MyBase` 是指直接基类和继承的成员。 不能用于访问`Private`类中的成员。  
  
-   `MyBase` 是关键字，而不是真实对象。 `MyBase` 不能分配给一个变量，传递给过程，或者使用在`Is`比较。  
  
-   该方法的`MyBase`限定无需在直接基类; 中定义而可能间接继承的基类中定义。 为了使由限定的引用`MyBase`正确编译，一些基类必须包含匹配的名称和类型的调用中出现的参数的方法。  
  
-   不能使用`MyBase`调用`MustOverride`基类方法。  
  
-   `MyBase` 不能用于限定本身。 因此，下面的代码不是有效的：  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase` 不能在模块中使用。  
  
-   `MyBase` 不能用于访问基类成员标记为`Friend`基类是否在不同的程序集。  
  
 有关详细信息和另一个示例，请参阅[如何：访问被派生类隐藏的变量](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。  
  
## <a name="the-myclass-keyword"></a>MyClass 关键字  
 `MyClass`关键字的行为方式类似于最初实现的类的当前实例是指的对象变量。 `MyClass` 类似于`Me`，但对每个方法和属性调用`MyClass`被看作方法或属性是[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)。 因此，该方法或属性是不受影响通过派生类中重写。  
  
-   `MyClass` 是关键字，而不是真实对象。 `MyClass` 不能分配给一个变量，传递给过程，或者使用在`Is`比较。  
  
-   `MyClass` 指包含类和其继承的成员。  
  
-   `MyClass` 可以使用与为限定符`Shared`成员。  
  
-   `MyClass` 无法在内部使用`Shared`方法，但可以使用实例方法内部来访问共享的成员的类。  
  
-   `MyClass` 不能在标准模块中使用。  
  
-   `MyClass` 可以用于限定基类中定义并具有在该类中提供的方法没有实现的方法。 此类引用与具有相同含义`MyBase.`*方法*。  
  
 下面的示例比较`Me`和`MyClass`。  
  
```vb
Class baseClass  
    Public Overridable Sub testMethod()  
        MsgBox("Base class string")  
    End Sub  
    Public Sub useMe()  
        ' The following call uses the calling class's method, even if   
        ' that method is an override.  
        Me.testMethod()  
    End Sub  
    Public Sub useMyClass()  
        ' The following call uses this instance's method and not any  
        ' override.  
        MyClass.testMethod()  
    End Sub  
End Class  
Class derivedClass : Inherits baseClass  
    Public Overrides Sub testMethod()  
        MsgBox("Derived class string")  
    End Sub  
End Class  
Class testClasses  
    Sub startHere()  
        Dim testObj As derivedClass = New derivedClass()  
        ' The following call displays "Derived class string".  
        testObj.useMe()  
        ' The following call displays "Base class string".  
        testObj.useMyClass()  
    End Sub  
End Class  
```  
  
 即使`derivedClass`重写`testMethod`，则`MyClass`中的关键字`useMyClass`使基类版本的调用无效的重写，而编译器解析效果`testMethod`。  
  
## <a name="see-also"></a>请参阅

- [Inherits 语句](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
