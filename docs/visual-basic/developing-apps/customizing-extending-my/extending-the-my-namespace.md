---
title: 扩展 Visual Basic 中的 My 命名空间
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 4d7bb6eef398746a4bd2dc4dbf3d526da1c1e0f1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814144"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>扩展 Visual Basic 中的 My 命名空间
`My`在 Visual Basic 中的命名空间公开属性和方法，您可以轻松地充分利用.NET Framework 的强大功能。 `My`命名空间简化了常见编程问题，通常可一行代码将一个困难的任务。 此外，`My`命名空间可完全扩展，使你可以自定义的行为`My`并将新的服务添加到其层次结构，以适应特定的应用程序需求。 本主题将讨论如何自定义的现有成员`My`命名空间以及如何添加到你自己自定义类`My`命名空间。  
  
 **主题内容**  
  
-   [自定义现有我 Namespace 成员](#customizing)  
  
-   [将成员添加到我的对象](#addingtoobjects)  
  
-   [自定义将对象添加到我 Namespace](#addingcustom)  
  
-   [将成员添加到我 Namespace](#addingtonamespace)  
  
-   [将事件添加到自定义 My 对象](#addingevents)  
  
-   [设计指南](#design)  
  
-   [设计的类库我](#designing)  
  
-   [打包和部署扩展](#packaging)  
  
## <a name="customizing"></a> 自定义现有我 Namespace 成员  
 `My`命名空间中 Visual Basic 公开经常使用你的应用程序、 您的计算机，和的详细信息。 有关中的对象的完整列表`My`命名空间，请参阅[我引用](../../../visual-basic/language-reference/keywords/my-reference.md)。 您可能要自定义的现有成员`My`命名空间，以便他们更好地匹配应用程序的需求。 中的对象的任何属性`My`命名空间不是只读的可以设置为自定义值。  
  
 例如，假定您经常使用`My.User`对象来访问运行应用程序的用户的当前安全上下文。 但是，你的公司使用自定义用户对象公开的其他信息和公司内的用户功能。 在此方案中，您可以替换的默认值`My.User.CurrentPrincipal`与您自己自定义主体对象，如下面的示例中所示的实例的属性。  
  
 [!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]  
  
 设置`CurrentPrincipal`属性上的`My.User`对象更改运行应用程序的标识。 `My.User`对象，就会返回有关新指定的用户的信息。  
  
## <a name="addingtoobjects"></a> 将成员添加到我的对象  
 从返回的类型`My.Application`并`My.Computer`定义为`Partial`类。 因此，您可以扩展`My.Application`并`My.Computer`通过创建对象`Partial`名为类`MyApplication`或`MyComputer`。 类不能是`Private`类。 如果您指定类的一部分`My`命名空间，可以添加属性和方法将附带`My.Application`或`My.Computer`对象。  
  
 例如，下面的示例添加名为的属性`DnsServerIPAddresses`到`My.Computer`对象。  
  
 [!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]  
  
## <a name="addingcustom"></a> 自定义将对象添加到我 Namespace  
 尽管`My`命名空间执行许多常见编程任务提供解决方案，可能会遇到的任务的`My`命名空间不能解决。 例如，你的应用程序可能会访问用户数据的自定义目录服务或应用程序可能使用不使用 Visual Basic 的默认情况下安装的程序集。 您可以扩展`My`命名空间以包含特定于你的环境的常见任务的自定义解决方案。 `My`命名空间可以轻松地进行扩展以添加新成员，以满足不断增长的应用程序需求。 此外，可以部署你`My`命名空间扩展到其他开发人员为 Visual Basic 模板。  
  
### <a name="addingtonamespace"></a> 将成员添加到我 Namespace  
 因为`My`是一个命名空间等任何其他命名空间，您可以顶级属性向其添加只需添加一个模块，并指定`Namespace`的`My`。 批注与模块`HideModuleName`特性，如以下示例所示。 `HideModuleName`属性可确保显示的成员时，IntelliSense 将不显示模块名称`My`命名空间。  
  
 [!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]  
  
 若要将成员添加到`My`命名空间中，根据需要向该模块添加属性。 每个属性添加到`My`命名空间中，添加类型的私有字段`ThreadSafeObjectProvider(Of T)`，其中类型是返回自定义属性的类型。 使用此字段来创建线程安全的对象实例通过调用返回的属性`GetInstance`方法。 因此，每个线程都访问扩展的属性接收它自己的返回类型的实例。 下面的示例添加名为的属性`SampleExtension`类型的`SampleExtension`到`My`命名空间：  
  
 [!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]  
  
## <a name="addingevents"></a> 将事件添加到自定义 My 对象  
 可以使用`My.Application`对象公开您的自定义事件`My`通过扩展对象`MyApplication`中的分部类`My`命名空间。 对于基于 Windows 的项目，你可以双击**我的项目**中的项目中的节点**解决方案资源管理器**。 在 Visual Basic**项目设计器**，单击`Application`选项卡，然后单击`View Application Events`按钮。 将创建名为 ApplicationEvents.vb 一个新文件。 它包含用于扩展的以下代码`MyApplication`类。  
  
 [!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]  
  
 你可以为您的自定义添加事件处理程序`My`对象添加到自定义事件处理程序`MyApplication`类。 自定义事件，可以添加一个事件处理程序添加、 删除或引发该事件时将执行的代码。 请注意，`AddHandler`由用户处理的事件添加代码的情况下，才会运行自定义事件的代码。 例如，考虑`SampleExtension`上文所述的对象具有`Load`你想要添加的自定义事件处理程序的事件。 下面的代码示例显示名为一个自定义事件处理程序`SampleExtensionLoad`会在调用时`My.SampleExtension.Load`事件发生。 当添加代码来处理新`My.SampleExtensionLoad`事件，`AddHandler`执行此自定义事件代码的一部分。 `MyApplication_SampleExtensionLoad`中的代码示例显示的事件处理程序处理的示例包含方法`My.SampleExtensionLoad`事件。 请注意，`SampleExtensionLoad`时选择，可以使用事件**我的应用程序事件**中左侧的下拉列表在代码编辑器上方编辑 ApplicationEvents.vb 文件时的选项。  
  
 [!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]  
  
## <a name="design"></a> 设计指南  
 开发扩展时`My`命名空间中，使用以下准则来帮助你扩展组件的维护成本降至最低。  
  
-   **包括仅扩展逻辑。** 包含的逻辑`My`命名空间扩展应包括仅公开在所需的功能所需的代码`My`命名空间。 因为您的扩展插件将驻留在用户项目为源代码，更新的扩展组件都会产生高额的维护成本，并应尽可能避免使用。  
  
-   **最小化项目的假设。** 当你创建的扩展`My`命名空间中，不要假设一组引用，项目级别导入或特定的编译器设置 (例如，`Option Strict`关闭)。 相反，最小化依赖项并使用完全限定所有类型引用`Global`关键字。 此外，请确保该扩展编译有`Option Strict`上以最大程度减少扩展中的错误。  
  
-   **隔离扩展插件代码。** 将代码放在一个文件使您的扩展插件可轻松部署为 Visual Studio 项模板。 有关详细信息，请参阅本主题后面的"打包和部署扩展"。 将所有`My`单个文件中的命名空间扩展插件代码或在项目中的单独文件夹还有助于用户查找`My`命名空间扩展。  
  
## <a name="designing"></a> 设计的类库我  
 对于多数对象模型情况一样，一些设计模式非常适合在`My`命名空间和其他人不这样做。 设计的扩展时`My`命名空间，请考虑以下原则：  
  
-   **无状态方法。** 中的方法`My`命名空间应提供某项特定任务的完整解决方案。 请确保传递给方法的参数值提供完成特定任务所需的所有输入。 避免创建依赖于以前的状态，如对资源的打开连接的方法。  
  
-   **全局实例。** 在中维护的唯一状态`My`命名空间是全局性的项目。 例如，`My.Application.Info`封装整个应用程序共享的状态。  
  
-   **简单的参数类型。** 为简单起见通过避免复杂的参数类型。 相反，创建不采取输入任何参数的方法或执行简单的输入的类型，如字符串、 基元类型和等等。  
  
-   **工厂方法。** 有些类型不一定困难，若要实例化。 提供工厂方法作为扩展`My`命名空间，可更轻松地发现和使用属于此类别的类型。 工厂方法，适合于的一个示例是`My.Computer.FileSystem.OpenTextFileReader`。 有多个流类型在.NET Framework 中可用。 具体而言，指定文本文件`OpenTextFileReader`可帮助用户了解要使用的流。  
  
 这些准则并不排除类库的常规设计原则。 相反，它们是针对使用的 Visual Basic 开发人员进行了优化的建议和`My`命名空间。 用于创建类库的常规设计原则，请参阅[Framework 设计准则](../../../standard/design-guidelines/index.md)。  
  
## <a name="packaging"></a> 打包和部署扩展  
 可以包括`My`命名空间扩展 Visual Studio 项目模板，或者您可以将扩展打包并将其部署为 Visual Studio 项模板。 当包在`My`为 Visual Studio 项模板的命名空间扩展，可以充分利用所提供的 Visual Basic 的其他功能。 这些功能让你可以在一个项目引用特定的程序集，包括了扩展，或使用户能够将显式添加你`My`使用的命名空间扩展**My 扩展**Visual Basic 的页项目设计器。  
  
 有关如何部署的详细信息`My`命名空间扩展，请参阅[打包和部署自定义 My 扩展](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)。  
  
## <a name="see-also"></a>请参阅

- [打包和部署自定义 My 扩展](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)
- [扩展 Visual Basic 应用程序模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [自定义 My 中可用的对象](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [“项目设计器”->“My 扩展”页](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [“项目设计器”->“应用程序”页 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
