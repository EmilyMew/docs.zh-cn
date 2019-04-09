---
title: TableLayoutPanel 控件概述
ms.date: 03/30/2017
f1_keywords:
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
ms.openlocfilehash: 57a57b9f888f2fc46eddba5b97b9e833a7e9f028
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134012"
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel 控件概述
<xref:System.Windows.Forms.TableLayoutPanel> 控件将其内容排列在网格中。 由于布局是同时在设计时和运行时执行的，因此它可随应用程序环境的变化而动态地变化。 这使得面板中的控件能够按比例调整大小，以便能够响应更改（例如父控件的大小调整或本地化产生的文本长度更改）。  
  
 任何 Windows 窗体控件均可以是 <xref:System.Windows.Forms.TableLayoutPanel> 控制的子控件，包括 <xref:System.Windows.Forms.TableLayoutPanel> 的其他实例。 这使你可以构造适应在运行时发生更改的复杂布局。  
  
 添加新控件时，<xref:System.Windows.Forms.TableLayoutPanel> 控件可扩展以容纳新控件，具体取决于 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>、<xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> 和 <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> 属性的值。 将 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> 或 <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> 属性的值设置为 0 指定将取消 <xref:System.Windows.Forms.TableLayoutPanel> 在相应方向的绑定。  
  
 在 <xref:System.Windows.Forms.TableLayoutPanel> 控件充满子控件后，还可控制扩展的方向（水平或垂直）。 默认情况下，<xref:System.Windows.Forms.TableLayoutPanel> 控件通过添加行向下扩展。  
  
 如果需要使行和列的行为不同于默认行为，可以通过使用 <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> 和 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> 属性来控制行和列的属性。 可分别设置行或列的属性。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> 控件将以下属性添加到其子控件中：`Cell`、`Column`、`Row`、`ColumnSpan` 和 `RowSpan`。  
  
 可以通过设置子控件上的 `ColumnSpan` 或 `RowSpan` 属性来合并 <xref:System.Windows.Forms.TableLayoutPanel> 控件中的单元格。  
  
1.  [如何：在 TableLayoutPanel 控件中对齐和拉伸控件](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [如何：在 TableLayoutPanel 控件中跨行和跨列](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [如何：在 TableLayoutPanel 控件中编辑行和列](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [演练：使用 TableLayoutPanel 在 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutSettings>
- [如何：设计非常适合本地化的 Windows 窗体布局](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [如何：创建可重设大小的 Windows 窗体以供输入数据](how-to-create-a-resizable-windows-form-for-data-entry.md)
- [TableLayoutPanel 控件的最佳做法](best-practices-for-the-tablelayoutpanel-control.md)
