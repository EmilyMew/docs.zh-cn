---
title: 如何：使用 BindingSource 和 INotifyPropertyChanged 接口引发更改通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 71fb0a09387c77dbc792180dac1b8594d11b3642
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119504"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>如何：使用 BindingSource 和 INotifyPropertyChanged 接口引发更改通知
<xref:System.Windows.Forms.BindingSource> 组件将在数据源中包含的类型实现 <xref:System.ComponentModel.INotifyPropertyChanged> 接口时自动删除数据源中的更改，并在属性值更改时引发 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件。 上述操作非常有用，因为已绑定到 <xref:System.Windows.Forms.BindingSource> 的控件之后会在数据源值更改时自动更新。  
  
> [!NOTE]
>  如果数据源实现 <xref:System.ComponentModel.INotifyPropertyChanged>，并且你正在执行异步操作，则不应更改后台线程上的数据源。 相反，应读取后台线程上的数据，并将数据合并到 UI 线程上的列表。  
  
## <a name="example"></a>示例  
 下面的代码示例演示了如何简单实现 <xref:System.ComponentModel.INotifyPropertyChanged> 接口。 它还演示了当将 <xref:System.Windows.Forms.BindingSource> 绑定到 <xref:System.ComponentModel.INotifyPropertyChanged> 类型的列表时，<xref:System.Windows.Forms.BindingSource> 如何将数据源更改自动传递到绑定控件。  
  
 如果使用 `CallerMemberName` 特性，则调用 `NotifyPropertyChanged` 方法不必将属性名称指定为字符串参数。 有关详细信息，请参阅[调用方信息 (C#)](../../../csharp/programming-guide/concepts/caller-information.md)或[调用方信息 (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md)。  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 System、System.Data、System.Drawing 和 System.Windows.Forms 程序集的引用。  
  
 Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。 另请参阅[如何：编译和运行完整的 Windows 窗体代码示例使用 Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb129228(v=vs.100))。  
  
## <a name="see-also"></a>请参阅

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [BindingSource 组件](bindingsource-component.md)
- [如何：使用 BindingSource ResetItem 方法引发更改通知](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
