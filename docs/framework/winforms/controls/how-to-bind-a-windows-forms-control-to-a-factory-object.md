---
title: 如何：将 Windows 窗体控件绑定到 Factory 对象
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 2de892d94afdfcdc580d20f90fb60ebabf4a9b37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093028"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a>如何：将 Windows 窗体控件绑定到 Factory 对象
生成与数据交互的控件时，有时需要将控件绑定到生成其他对象的对象或方法。 此类对象或方法被称为 Factory。 例如，数据源可能是方法调用的返回值，而不是内存中的对象或类型。 只要源返回集合，即可将控件绑定到此类数据源。  
  
 借助 <xref:System.Windows.Forms.BindingSource> 控件可轻松将控件绑定到工厂对象。  
  
## <a name="example"></a>示例  
 下面的示例演示了如何使用 <xref:System.Windows.Forms.BindingSource> 控件将 <xref:System.Windows.Forms.DataGridView> 控件绑定到工厂方法。 Factory 方法命名为 `GetOrdersByCustomerId`，并返回 Northwind 数据库中给定客户的所有订单。  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
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
