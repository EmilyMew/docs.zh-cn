---
title: 演练：调用 Windows Api (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
ms.openlocfilehash: 579da4b52a9a7c4c747a9ace390c04611207c94d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822903"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>演练：调用 Windows Api (Visual Basic)
Windows Api 是动态链接库 (Dll) 的 Windows 操作系统的一部分。 您可以使用它们来执行任务时很难编写你自己的等效过程。 例如，Windows 提供了一个名为函数`FlashWindowEx`允许您进行应用程序的标题栏在浅色和深色阴影之间切换。  
  
 在代码中使用 Windows Api 的优点是它们可以节省开发时间，因为它们包含大量有用的功能，已编写并等待使用。 缺点是 Windows Api 可能很难处理和铁面无私时出现问题。  
  
 Windows Api 表示一类特殊的互操作性。 Windows Api 不使用托管的代码，没有内置类型库，并使用不同于与用于 Visual Studio 的数据类型。 鉴于这些区别，因为 Windows Api 不是 COM 对象，与 Windows Api 互操作性和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]使用平台执行的调用，简称 PInvoke。 平台调用是一项服务，它使托管代码能够调用非托管的 Dll 中实现的函数。 有关详细信息，请参阅[使用非托管 DLL 函数](../../../framework/interop/consuming-unmanaged-dll-functions.md)。 可以通过使用 Visual Basic 中使用 PInvoke`Declare`语句或将应用`DllImport`属性为空的过程。  
  
 Windows API 调用了 Visual Basic 编程在过去，一个重要部分，但很少需要使用 Visual Basic.NET。 只要有可能，应使用从托管的代码[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]来执行任务，而不是 Windows API 调用。 本演练提供了哪些使用那些情况的信息是必需的 Windows Api。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>使用 API 调用声明  
 调用 Windows Api 的最常见方法是使用`Declare`语句。  
  
#### <a name="to-declare-a-dll-procedure"></a>若要声明 DLL 过程  
  
1.  确定你想要调用，该函数及其参数、 参数类型的名称和返回值，以及名称和包含该 DLL 的位置。  
  
    > [!NOTE]
    >  有关 Windows Api 的完整信息，请参阅平台 SDK Windows API 中的 Win32 SDK 文档。 有关 Windows Api 使用的常量的详细信息，检查如 Windows.h Platform SDK 中包含的标头文件。  
  
2.  通过单击打开一个新的 Windows 应用程序项目**新建**上**文件**菜单中，然后单击**项目**。 此时将出现“新建项目”对话框。  
  
3.  选择**Windows 应用程序**从 Visual Basic 项目模板的列表。 显示新的项目。  
  
4.  以下代码添加到`Declare`函数到类或想要使用该 DLL 的模块：  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>部件的 Declare 语句  
 `Declare`语句包括以下元素。  
  
#### <a name="auto-modifier"></a>Auto 修饰符  
 `Auto`修饰符指示运行时转换基于根据公共语言运行时规则 （或已指定的别名） 的方法名称的字符串。  
  
#### <a name="lib-and-alias-keywords"></a>Lib 和别名关键字  
 名称以下`Function`关键字是您的程序用来访问导入的函数的名称。 它可以是你要调用的函数的真实名称相同，也可以使用任何有效的过程名称，然后使用`Alias`关键字来指定要调用的函数的真实名称。  
  
 指定`Lib`关键字后, 跟的名称和包含要调用的函数的 DLL 的位置。 不需要指定位于 Windows 系统目录中文件的路径。  
  
 使用`Alias`关键字，如果你正在调用的函数的名称不是有效的 Visual Basic 过程名称，或与你的应用程序中其他项的名称冲突。 `Alias` 指示要调用的函数的真实名称。  
  
#### <a name="argument-and-data-type-declarations"></a>参数和数据类型声明  
 声明的参数和其数据类型。 此部分会很困难，因为 Windows 使用的数据类型不对应于 Visual Studio 的数据类型。 Visual Basic 通过将参数转换为兼容的数据类型，名为的过程为您完成大量工作*封送处理*。 您可以显式控制参数使用被封送<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性中定义<xref:System.Runtime.InteropServices>命名空间。  
  
> [!NOTE]
>  Visual Basic 的早期版本允许您声明参数`As Any`，这意味着该数据的任何数据就可以使用类型。 Visual Basic 要求您对所有使用特定的数据类型`Declare`语句。  
  
#### <a name="windows-api-constants"></a>Windows API 常量  
 某些参数是常量的组合。 例如，`MessageBox`在本演练中所示的 API 接受整数参数名为`Typ`，它控制如何显示消息框。 可以通过检查来确定这些常量的数值`#define`文件 WinUser.h 中的语句。 以十六进制格式，通常显示的数字值，因此可能需要使用一个计算器来将它们添加并将转换为十进制。 例如，如果想要合并的感叹号样式的常量`MB_ICONEXCLAMATION`0x00000030 和是/无样式`MB_YESNO`0x00000004，可以添加数字并获取结果 0x00000034 52 十进制。 虽然可以直接使用十进制的结果，则最好将这些值声明为你的应用程序中的常量并将其组合使用`Or`运算符。  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>若要声明常量 Windows API 调用  
  
1.  要调用的 Windows 函数，请参阅文档。 确定使用的常数的名称以及包含这些常量的数值的.h 文件的名称。  
  
2.  使用文本编辑器，如记事本，若要查看的内容标头 (.h) 文件，并查找与正在使用的常量相关联的值。 例如， `MessageBox` API 使用常量`MB_ICONQUESTION`在消息框中显示一个问号。 有关定义`MB_ICONQUESTION`是在 WinUser.h 中，将出现，如下所示：  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  添加等效`Const`到类或模块，以使这些常量可用于应用程序的语句。 例如：  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>若要调用的 DLL 过程  
  
1.  添加名为的按钮`Button1`启动窗体让你的项目，然后双击它以查看其代码。 显示按钮的事件处理程序。  
  
2.  将代码添加到`Click`您添加的按钮，调用该过程，并提供适当的参数的事件处理程序：  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3.  通过按 F5 运行项目。 消息框显示两个**是**并**否**响应按钮。 单击其中任何一个。  
  
#### <a name="data-marshaling"></a>数据封送处理  
 Visual Basic 会自动将转换的数据类型的参数和返回值为 Windows API 调用，但你可以使用`MarshalAs`属性来显式指定 API 预期的非托管的数据类型。 关于互操作封送处理的详细信息，请参阅[互操作封送处理](../../../framework/interop/interop-marshaling.md)。  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>若要在 API 调用中使用 Declare 和 MarshalAs  
  
1.  确定你想要的参数、 调用数据类型的函数的名称和返回值。  
  
2.  若要简化对访问`MarshalAs`特性，请添加`Imports`到类或模块，如以下示例所示的代码的顶部的语句：  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3.  将导入的函数的函数原型添加到类或模块使用的，并应用`MarshalAs`属性为参数或返回值。 在下面的示例中，需要类型的 API 调用`void*`被封送为`AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>使用 DllImport 的 API 调用  
 `DllImport`属性提供不带类型库在 Dll 中调用函数的第二个方法。 `DllImport` 大致相当于使用`Declare`语句，但可以更好地控制函数的调用方式。  
  
 可以使用`DllImport`与大多数 Windows API 调用，只要该调用是指在不共享 (有时称为*静态*) 方法。 不能使用需要的类实例的方法。 与不同`Declare`语句，`DllImport`的调用不能使用`MarshalAs`属性。  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>若要调用 Windows API 使用 DllImport 特性  
  
1.  通过单击打开一个新的 Windows 应用程序项目**新建**上**文件**菜单中，然后单击**项目**。 此时将出现“新建项目”对话框。  
  
2.  选择**Windows 应用程序**从 Visual Basic 项目模板的列表。 显示新的项目。  
  
3.  添加名为的按钮`Button2`到启动窗体。  
  
4.  双击`Button2`以打开窗体的代码视图。  
  
5.  若要简化对访问`DllImport`，添加`Imports`语句启动窗体类的代码的顶部：  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6.  声明一个空的函数，前面`End Class`窗体，并将函数命名为语句`MoveFile`。  
  
7.  将应用`Public`并`Shared`函数声明和设置的参数的修饰符`MoveFile`根据 Windows API 函数使用的参数：  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     你的函数名称可以是任意有效的过程;`DllImport`属性在 DLL 中指定的名称。 它还处理互操作封送处理参数和返回值，因此，可以选择 Visual Studio 的数据类型类似于数据的类型 API 使用。  
  
8.  将应用`DllImport`属性为空函数。 第一个参数是名称和包含要调用的函数的 dll 的位置。 不需要指定位于 Windows 系统目录中文件的路径。 第二个参数是函数的命名的参数，Windows API 中指定的名称。 在此示例中，`DllImport`属性强制调用`MoveFile`转发到`MoveFileW`KERNEL32 中。DLL。 `MoveFileW`方法将文件复制从路径`src`到路径`dst`。  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. 将代码添加到`Button2_Click`事件处理程序调用该函数：  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. 创建一个名为 Test.txt 文件并将其放在硬盘上 C:\Tmp 目录中。 如有必要，请创建临时目录。  
  
11. 按 F5 键启动该应用程序。 主窗体显示。  
  
12. 单击**Button2**。 如果可以移动该文件，则会显示"文件已移动已成功"消息。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Declare 语句](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)
- [COM 互操作](../../../visual-basic/programming-guide/com-interop/index.md)
- [在托管代码中创建原型](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [将委托作为回调方法进行封送](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
