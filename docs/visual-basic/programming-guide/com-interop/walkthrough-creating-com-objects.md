---
title: 演练：使用 Visual Basic 创建 COM 对象
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 5fc0105cffb5606f9382aca7b55d6544d04f9fe7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838152"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>演练：使用 Visual Basic 创建 COM 对象
创建新的应用程序或组件时，最好创建.NET Framework 程序集。 但是，Visual Basic 还可以轻松公开.NET Framework 组件由 com 使用。 这使您可以提供新的组件需要 COM 组件的早期应用程序套件。 本演练演示如何使用 Visual Basic 来公开[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]对象作为 COM 对象，使用或不使用 COM 类模板。  
  
 若要公开的 COM 对象的最简单方法是使用 COM 类模板。 使用 COM 类模板创建一个新类，然后配置你的项目以生成为 COM 对象的类和互操作性层，并将其注册到操作系统。  
  
> [!NOTE]
>  尽管您可以公开为 COM 对象以供使用的非托管代码在 Visual Basic 中创建的类，但它不是真正的 COM 对象并不能使用 Visual basic。 有关详细信息，请参阅[.NET Framework 应用程序中的 COM 互操作性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>若要使用 COM 类模板创建 COM 对象  
  
1.  打开一个新的 Windows 应用程序项目，从**文件**菜单中单击**新项目**。  
  
2.  在中**新的项目**对话框中的下**项目类型**字段中，检查是否已选中 Windows。 选择**类库**从**模板**列表，，然后单击**确定**。 显示新的项目。  
  
3.  选择**添加新项**从**项目**菜单。 随即出现“添加新项”对话框。  
  
4.  选择**COM 类**从**模板**列表，，然后单击**添加**。 Visual Basic 将添加一个新类和配置 COM 互操作的新项目。  
  
5.  如属性、 方法和事件的代码添加到 COM 类。  
  
6.  选择**生成 ClassLibrary1**从**生成**菜单。 Visual Basic 生成的程序集和与操作系统中注册的 COM 对象。  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>创建 COM 对象不使用 COM 类模板  
 此外可以创建一个手动而不是使用 COM 类模板的 COM 类。 从命令行工作时或当你想更好地控制如何定义 COM 对象时，此过程非常有用。  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>要将你的项目设置为生成的 COM 对象  
  
1.  打开一个新的 Windows 应用程序项目，从**文件**菜单中单击**NewProject**。  
  
2.  在中**新的项目**对话框中的下**项目类型**字段中，检查是否已选中 Windows。 选择**类库**从**模板**列表，，然后单击**确定**。 显示新的项目。  
  
3.  在“解决方案资源管理器”中，右键单击项目，然后单击“属性”。 **项目设计器**显示。  
  
4.  单击“编译”选项卡。  
  
5.  选择**为 COM 互操作注册**复选框。  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>若要设置您的类中的代码创建 COM 对象  
  
1.  在中**解决方案资源管理器**，双击**Class1.vb**以显示其代码。  
  
2.  将该类重命名为 `ComClass1`。  
  
3.  添加到以下常量`ComClass1`。 它们将存储不需要具有 COM 对象的全局唯一标识符 (GUID) 常量。  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4.  在“工具”菜单上，单击“创建 Guid”。 在“创建 GUID”对话框中，单击“注册表格式”，然后单击“复制”。 单击“退出” 。  
  
5.  空字符串替换为`ClassId`guid，删除前导空格和尾随大括号。 例如，如果由 Guidgen 提供的 GUID 是`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`，则你的代码应如下所示出现。  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6.  重复前面的步骤对于`InterfaceId`和`EventsId`常量，如以下示例所示。  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    >  请确保 Guid 的新的和唯一的;否则，COM 组件可能与其他 COM 组件发生冲突。  
  
7.  添加`ComClass`属性为`ComClass1`，指定为类 ID、 接口 ID 和事件 ID 的 Guid，如以下示例所示：  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8.  COM 类必须具有无参数`Public Sub New()`构造函数或类无法正确注册。 将无参数构造函数添加到类：  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. 将属性、 方法和事件添加到类，它与结束`End Class`语句。 选择**生成解决方案**从**生成**菜单。 Visual Basic 生成的程序集和与操作系统中注册的 COM 对象。  
  
    > [!NOTE]
    >  使用 Visual Basic 生成的 COM 对象不能使用其他 Visual Basic 应用程序，因为它们不是真正的 COM 对象。 尝试将引用添加到此类 COM 对象将引发错误。 有关详细信息，请参阅[.NET Framework 应用程序中的 COM 互操作性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [COM 互操作](../../../visual-basic/programming-guide/com-interop/index.md)
- [演练：使用 COM 对象实现继承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [#Region 指令](../../../visual-basic/language-reference/directives/region-directive.md)
- [.NET Framework 应用程序中的 COM 互操作性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [互操作性疑难解答](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
