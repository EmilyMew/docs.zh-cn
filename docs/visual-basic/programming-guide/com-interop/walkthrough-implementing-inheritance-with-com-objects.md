---
title: 演练：使用 COM 对象 (Visual Basic 中) 实现继承
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: ee7258a78ad0a434bfad08eebd596a8b889e2304
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826166"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>演练：使用 COM 对象 (Visual Basic 中) 实现继承
您可以从 Visual Basic 类进行派生`Public`中 COM 对象，即使这些早期版本的 Visual Basic 中创建的类。 可以重写或重载只是作为属性的属性和方法从 COM 对象继承的类和任何其他基类的方法可以重写或重载。 具有不希望重新编译现有类库时，从 COM 对象的继承非常有用。  
  
 以下过程说明如何使用 Visual Basic 6.0 创建包含的类的 COM 对象，然后将其用作基类。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>若要生成本演练中使用的 COM 对象  
  
1.  在 Visual Basic 6.0 中，打开一个新的 ActiveX DLL 项目。 一个名为项目`Project1`创建。 它具有一个名为类`Class1`。  
  
2.  在中**项目资源管理器**，右键单击**Project1**，然后单击**Project1 属性**。 **项目属性**显示对话框。  
  
3.  上**常规**选项卡**项目属性**对话框框中，通过键入更改项目名称`ComObject1`中**项目名称**字段。  
  
4.  在中**项目资源管理器**，右键单击`Class1`，然后单击**属性**。 **属性**显示窗口中的类。  
  
5.  更改`Name`属性设置为`MathFunctions`。  
  
6.  在中**项目资源管理器**，右键单击`MathFunctions`，然后单击**查看代码**。 **代码编辑器**显示。  
  
7.  添加一个本地变量来保存属性值：  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  将属性添加`Let`和属性`Get`属性过程：  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. 添加函数：  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. 创建并注册的 COM 对象，通过单击**使 ComObject1.dll**上**文件**菜单。  
  
    > [!NOTE]
    >  尽管您可以公开为 COM 对象的 Visual basic 创建的类，但它不是真正的 COM 对象并不能在本演练中使用。 有关详细信息，请参阅[.NET Framework 应用程序中的 COM 互操作性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
## <a name="interop-assemblies"></a>互操作程序集  
 在下面的过程中，您将创建一个互操作程序集，它作为非托管的代码 （如 COM 对象） 和 Visual Studio 使用的托管的代码之间的桥梁。 Visual Basic 创建的互操作程序集处理的详细信息，如使用 COM 对象的大部分*互操作封送处理*，打包参数和返回值为等效的数据的进程类型，因为它们将移动到和从 COM 对象。 在 Visual Basic 应用程序中的引用所指向的互操作程序集，不是实际的 COM 对象。  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>若要使用 Visual Basic 2005 和更高版本的 COM 对象  
  
1.  打开一个新的 Visual Basic Windows 应用程序项目。  
  
2.  在“项目”菜单上，单击“添加引用”。  
  
     将显示“添加引用”对话框。  
  
3.  上**COM**选项卡上，双击`ComObject1`中**组件名称**列表，然后单击**确定**。  
  
4.  在 **“项目”** 菜单上，单击 **“添加新项”**。  
  
     随即出现“添加新项”对话框。  
  
5.  在中**模板**窗格中，单击**类**。  
  
     默认文件名的名称， `Class1.vb`，将出现在**名称**字段。 将此字段更改为 MathClass.vb，然后单击**添加**。 这将创建一个名为类`MathClass`，并显示其代码。  
  
6.  将以下代码添加到顶部`MathClass`从 COM 类继承。  
  
     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]  
  
7.  以下代码添加到重载的基类的公共方法`MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]  
  
8.  通过添加以下代码来扩展继承的类`MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]  
  
 新类继承的基类中的 COM 对象的属性、 重载方法，并定义用于扩展类的新方法。  
  
#### <a name="to-test-the-inherited-class"></a>若要测试继承的类  
  
1.  启动窗体中，添加一个按钮，然后双击它以查看其代码。  
  
2.  在按钮的`Click`事件处理程序过程中，添加以下代码创建的实例`MathClass`和调用重载的方法：  
  
     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]  
  
3.  通过按 F5 运行项目。  
  
 单击窗体上的按钮时`AddNumbers`方法首先调用的`Short`数据键入数字和 Visual Basic 会从基类中选择相应的方法。 第二次调用`AddNumbers`定向到从重载方法`MathClass`。 第三个调用调用`SubtractNumbers`方法，它扩展了类。 设置基类中的属性，并显示的值。  
  
## <a name="next-steps"></a>后续步骤  
 您可能已经注意到，重载`AddNumbers`函数显示为具有相同的数据类型从 COM 对象的基类继承的方法。 这是因为参数和基类方法的参数定义为 16 位整数，在 Visual Basic 6.0 中，但它们公开为 16 位整数类型的`Short`更高版本的 Visual Basic 中。 新函数接受 32 位整数，并重载基类函数。  
  
 当使用 COM 对象，请确保验证参数的大小和数据类型。 例如，当使用接受作为自变量的 Visual Basic 6.0 集合对象的 COM 对象时，不能提供更高版本的 Visual Basic 中的集合。  
  
 属性和方法继承自 COM 类可以重写，这意味着您可以声明的本地属性或方法来代替属性或继承自基类的 COM 类的方法。 重写继承的 COM 属性的规则包括类似于重写其他属性和方法有以下例外规则：  
  
-   如果重写任何属性或方法从 COM 类继承，则必须重写所有其他继承的属性和方法。  
  
-   使用属性`ByRef`参数不能重写。  
  
## <a name="see-also"></a>请参阅

- [.NET Framework 应用程序中的 COM 互操作性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Inherits 语句](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Short 数据类型](../../../visual-basic/language-reference/data-types/short-data-type.md)
