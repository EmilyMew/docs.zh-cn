---
title: PrintPreviewDialog 控件概述（Windows 窗体）
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32fbdd222e34f642d29255e6c594076b6d2a91e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188833"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog 控件概述 （Windows 窗体）
Windows 窗体<xref:System.Windows.Forms.PrintPreviewDialog>控件是一个预配置的对话框，用于显示如何[PrintDocument](printdocument-component-windows-forms.md)打印时的显示。 为简单的解决方案，而不是配置你自己的对话框在基于 Windows 的应用程序中使用它。 该控件包含用于打印、放大、显示一页或多页以及关闭对话框的按钮。  
  
## <a name="key-properties-and-methods"></a>键属性和方法  
 控件的关键属性是<xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>，用于设置要预览的文档。 文档必须是<xref:System.Drawing.Printing.PrintDocument>对象。 为了显示对话框中，您必须调用其<xref:System.Windows.Forms.Form.ShowDialog%2A>方法。 抗锯齿功能可以使文本显示更加顺利，但它还可以显示更慢;若要使用它，将设置<xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A>属性设置为`true`。  
  
 某些属性是可通过<xref:System.Windows.Forms.PrintPreviewControl>的<xref:System.Windows.Forms.PrintPreviewDialog>包含。 (无需添加这<xref:System.Windows.Forms.PrintPreviewControl>向窗体; 它会自动包含在<xref:System.Windows.Forms.PrintPreviewDialog>向窗体添加对话框时。)可通过属性的示例<xref:System.Windows.Forms.PrintPreviewControl>都<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>和<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>属性，确定在控件上显示水平和垂直方向的页面数。 您可以访问<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>属性设置为`PrintPreviewDialog1.PrintPreviewControl.Columns`在 Visual Basic`printPreviewDialog1.PrintPreviewControl.Columns`视觉对象中C#，或`printPreviewDialog1->PrintPreviewControl->Columns`中[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]。  
  
## <a name="printpreviewdialog-performance"></a>PrintPreviewDialog 性能

在以下情况下<xref:System.Windows.Forms.PrintPreviewDialog>控件初始化非常缓慢：

- 使用网络打印机。
- 修改此打印机，如双面打印设置的用户首选项。
  
对于.NET Framework 4.5.2 上运行的应用程序，可以添加的以下关键\<appSettings > 配置文件来提高的性能的部分<xref:System.Windows.Forms.PrintPreviewDialog>控制初始化：

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
如果`EnablePrintPreviewOptimization`键设置为任何其他值，或如果密钥不存在，则不会应用优化。

对于.NET Framework 4.6 或更高版本上运行的应用程序，您可以添加到以下开关[ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)中的元素[\<运行时 >](../../configure-apps/file-schema/runtime/index.md)应用程序配置文件的部分：

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
如果交换机不存在，或者设置为任何其他值，则不会应用优化。 

如果您使用<xref:System.Drawing.Printing.PrintDocument.QueryPageSettings>要修改的打印机设置的性能事件<xref:System.Windows.Forms.PrintPreviewDialog>控件不会提高，即使设置优化配置开关。  

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [PrintPreviewControl 控件概述](printpreviewcontrol-control-overview-windows-forms.md)
- [PrintPreviewDialog 控件](printpreviewdialog-control-windows-forms.md)
- [对话框控件和组件](dialog-box-controls-and-components-windows-forms.md)
