---
title: 结构和类 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: 3635729705520518d4c950f8a79da7d1249285bf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841610"
---
# <a name="structures-and-classes-visual-basic"></a>结构和类 (Visual Basic)
Visual Basic 统一的结构和类，因此这两个实体支持的大多数功能相同的语法。 但是，也有重要区别结构和类。  
  
 类具有的优点是引用类型，传递一个引用是传递的所有数据的结构变量比效率更高。 但是，结构不需要全局堆上的内存的分配。  
  
 由于不能继承自一个结构，结构仅应该用于不需要进行扩展的对象。 当你想要创建的对象具有小型实例大小，并考虑类和结构的性能特征，请使用结构。  
  
## <a name="similarities"></a>相似之处  
 结构和类是在以下方面类似：  
  
-   两者都*容器*类型，这意味着它们包含其他类型作为成员。  
  
-   都具有成员，它们可以包括构造函数、 方法、 属性、 字段、 常量、 枚举、 事件和事件处理程序。 但是，不要混淆的已声明这些成员*元素*的结构。  
  
-   这两者的成员可以分别有不同的访问级别。 例如，可以声明一个成员`Public`和另一个`Private`。  
  
-   同时可以实现接口。  
  
-   使用或不带参数，都可以具有共享构造函数。  
  
-   两者都可以公开*默认属性*，前提是该属性带有至少一个参数。  
  
-   同时可以声明和引发事件，并且两者都可以声明委托。  
  
## <a name="differences"></a>差异  
 结构和类在以下方面有所不同：  
  
-   结构是否*值类型*; 类是*引用类型*。 结构类型的变量包含结构的数据，而不是那样包含对将数据作为类类型的引用。  
  
-   结构使用堆栈分配;类使用堆分配。  
  
-   结构的所有元素都都`Public`默认情况下; 类变量和都常量`Private`默认情况下，而其他类成员都是`Public`默认情况下。 此行为对于类成员提供了与默认值的 Visual Basic 6.0 系统的兼容性。  
  
-   一种结构必须具有至少一个非共享变量或非共享、 非自定义事件的元素;一个类可以是完全为空。  
  
-   结构元素不能声明为`Protected`; 可以类成员。  
  
-   结构过程可以处理事件，仅当[共享](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub`过程中，并仅通过的方式[AddHandler 语句](../../../../visual-basic/language-reference/statements/addhandler-statement.md); 任何类的过程可以处理事件，使用任一[处理](../../../../visual-basic/language-reference/statements/handles-clause.md)关键字或`AddHandler`语句。 有关详细信息，请参阅[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。  
  
-   结构变量声明不能指定初始值设定项或数组; 的初始大小类的变量声明可以。  
  
-   结构隐式继承自<xref:System.ValueType?displayProperty=nameWithType>类，并从任何其他类型; 不能继承类可以继承自任何类或类以外<xref:System.ValueType?displayProperty=nameWithType>。  
  
-   结构是不可继承;类是。  
  
-   永远不会终止结构，因此公共语言运行时 (CLR) 永远不会调用<xref:System.Object.Finalize%2A>任何结构; 方法由垃圾回收器 (GC)，它调用终止类<xref:System.Object.Finalize%2A>上检测到有任何活动的引用时的类剩余。  
  
-   结构不需要构造函数;类一样。  
  
-   结构可以具有非共享的构造函数仅当它们采用参数;类可以让它们使用或不带参数。  
  
 每个结构具有不带参数的隐式公共构造函数。 此构造函数初始化结构的所有数据元素为其默认值。 不能重新定义此行为。  
  
## <a name="instances-and-variables"></a>实例和变量  
 由于结构是值类型，每个结构变量是永久绑定到单个结构实例。 类是引用类型，但对象变量可以在不同时间指不同的类实例。 这一区别在通过以下方式影响你的结构和类的使用情况：  
  
-   **初始化。** 结构变量隐式包含使用该结构的无参数构造函数的元素的初始化。 因此，`Dim s As struct1`等效于`Dim s As struct1 = New struct1()`。  
  
-   **分配变量。** 当您将一个结构变量分配到另一个，或将结构实例传递给过程自变量时，变量的所有元素的当前值复制到新结构。 当将一个对象变量分配给另一个，或将对象变量传递给过程时，复制仅引用指针。  
  
-   **分配执行任何操作。** 可以分配值[Nothing](../../../../visual-basic/language-reference/nothing.md)为结构变量，但该实例将继续与变量相关联。 仍可以调用其方法和访问其数据元素，但变量元素被重新初始化由赋值。  
  
     相反，如果对象变量设置为`Nothing`、 取消关联任何类的实例，并不能通过变量访问任何成员，直到将另一个实例分配给它。  
  
-   **多个实例。** 对象变量可以在不同的时间，赋给它的另一个类实例，并且多个对象变量可以在同一时间引用相同的类实例。 对类成员的值所做的更改会影响时通过指向同一个实例的另一个变量来访问这些成员。  
  
     结构元素，但是，是独立于其自身实例。 为其值的更改未反映在任何其他结构变量，即使在相同的其他实例中`Structure`声明。  
  
-   **相等。** 逐个元素测试，必须执行两个结构相等性测试。 可以使用比较两个对象变量<xref:System.Object.Equals%2A>方法。 <xref:System.Object.Equals%2A> 指示两个变量是否指向同一个实例。  
  
## <a name="see-also"></a>请参阅

- [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [复合数据类型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [结构](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [数据类型疑难解答](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [结构和其他编程元素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [对象和类](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
