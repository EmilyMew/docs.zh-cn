---
title: 如何：调用打印对话框
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 038e259810111d2d648c72a9f43afabe11a07f29
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358426"
---
# <a name="how-to-invoke-a-print-dialog"></a>如何：调用打印对话框
若要提供从你应用程序打印的功能，可以只需创建和打开<xref:System.Windows.Controls.PrintDialog>对象。  
  
## <a name="example"></a>示例  
 <xref:System.Windows.Controls.PrintDialog> 控件为 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、配置和 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 作业提交提供单一入口点。 该控件是易于使用，可以通过使用实例化[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]标记或代码。 下面的示例演示如何实例化并在 code 中打开该控件以及如何从其打印。 它还演示如何以确保设置特定范围的页面的选项的对话框会给用户。 此代码示例假定 c： 驱动器的根目录中的文件 FixedDocumentSequence.xps。  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 打开对话框后，用户将能够从他们的计算机上安装的打印机中选择。 此外将选择的选项[Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)若要创建[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]文件而不是打印。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>控制[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，本主题中对其进行讨论不应混淆与<xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType>Windows 窗体的组件。  
  
 严格地说，您可以使用<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>甚至不用打开对话框的方法。 在此意义上，控件可用作不可见的打印组件。 但出于性能原因，它会更好的做法可以使用两种<xref:System.Printing.PrintQueue.AddJob%2A>方法或多个<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>并<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法的<xref:System.Windows.Xps.XpsDocumentWriter>。 有关详细信息，请参阅[以编程方式打印 XPS 文件](how-to-programmatically-print-xps-files.md)和。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Controls.PrintDialog>
- [WPF 中的文档](documents-in-wpf.md)
- [打印概述](printing-overview.md)
- [Microsoft XPS 文档编写器](https://go.microsoft.com/fwlink/?LinkId=147319)
