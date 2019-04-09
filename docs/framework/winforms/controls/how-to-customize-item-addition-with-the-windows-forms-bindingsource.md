---
title: 如何：使用 Windows 窗体 BindingSource 自定义项添加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 0a2f8491d0f027ca834257e2ec3a08d0b8bdb7ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129541"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>如何：使用 Windows 窗体 BindingSource 自定义项添加
使用 <xref:System.Windows.Forms.BindingSource> 组件将 Windows 窗体控件绑定到数据源时，可能会发现需要自定义新项目的创建。 <xref:System.Windows.Forms.BindingSource> 组件通过提供 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件（通常在绑定的控件需要创建新项目时引发）使这种情况简单明了。 事件处理程序可以提供所需的任何自定义行为（例如，在 Web 服务上调用方法或从类工厂中获取新对象）。  
  
> [!NOTE]
>  通过处理 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件添加项时，无法取消该添加。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 <xref:System.Windows.Forms.DataGridView> 组件将 <xref:System.Windows.Forms.BindingSource> 控件绑定到类工厂。 用户单击 <xref:System.Windows.Forms.DataGridView> 控件的新行时，引发 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件。 事件处理程序创建一个新 `DemoCustomer` 对象，该对象被分配至 <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> 属性。 这将导致新 `DemoCustomer` 对象被添加到 <xref:System.Windows.Forms.BindingSource> 组件的列表中和显示在 <xref:System.Windows.Forms.DataGridView> 控件的新行中。  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 System、System.Data、System.Drawing 和 System.Windows.Forms 程序集的引用。  
  
 Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource 组件](bindingsource-component.md)
- [如何：将 Windows 窗体控件绑定到类型](how-to-bind-a-windows-forms-control-to-a-type.md)
