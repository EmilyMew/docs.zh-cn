---
title: PrintPreviewControl 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: e9f1c2ae912b6beeba70c318b94a3052e2f99acb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122494"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl 控件概述（Windows 窗体）
Windows 窗体<xref:System.Windows.Forms.PrintPreviewControl>用来显示[PrintDocument](printdocument-component-windows-forms.md)打印时将显示。 此控件具有没有按钮或其他用户界面元素，因此通常仅在你想要编写自己的打印预览用户界面时才使用 <xref:System.Windows.Forms.PrintPreviewControl>。 如果您希望的标准用户界面，使用<xref:System.Windows.Forms.PrintPreviewDialog>控制; 请参阅[PrintPreviewDialog 控件概述](printpreviewdialog-control-overview-windows-forms.md)概述。  
  
## <a name="key-properties"></a>键属性  
 控件的关键属性是<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>，用于设置要预览的文档。 文档必须是<xref:System.Drawing.Printing.PrintDocument>对象。 创建进行打印的文档的概述，请参阅[PrintDocument 组件概述](printdocument-component-overview-windows-forms.md)并[Windows 窗体打印支持](../advanced/windows-forms-print-support.md)。 <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>和<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>属性确定的水平和垂直显示在控件上的页数。 抗锯齿功能可以使文本显示更加顺利，但它还可以显示更慢;若要使用它，将设置<xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A>属性设置为`true`。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.PrintPreviewControl>
- [PrintPreviewDialog 控件概述](printpreviewdialog-control-overview-windows-forms.md)
- [PrintPreviewControl 控件](printpreviewcontrol-control-windows-forms.md)
- [对话框控件和组件](dialog-box-controls-and-components-windows-forms.md)
