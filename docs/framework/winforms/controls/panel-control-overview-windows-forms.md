---
title: Panel 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: d4976b3725d04162ac10242c486f57c4d2598769
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086359"
---
# <a name="panel-control-overview-windows-forms"></a>Panel 控件概述（Windows 窗体）
Windows 窗体<xref:System.Windows.Forms.Panel>控件用于提供可识别分组其他控件。 通常情况下，您可以使用面板按功能细分窗体。 例如，可以指定邮件的选项，如使用哪些通宵运输工具的订单窗体。 分组面板中的所有选项为用户提供一个逻辑的视觉提示。 在设计时控件可以轻松地移动所有 — 在移动时<xref:System.Windows.Forms.Panel>控制，所有其包含的控件移动，过。 可以通过访问面板中进行分组的控件及其<xref:System.Windows.Forms.Control.Controls%2A>属性。 此属性返回的集合<xref:System.Windows.Forms.Control>检索这种方式为其特定类型实例，因此通常需要强制转换控件。  
  
## <a name="panel-versus-groupbox"></a>与分组框的面板  
 <xref:System.Windows.Forms.Panel>控件是类似于<xref:System.Windows.Forms.GroupBox>控制; 但是，仅<xref:System.Windows.Forms.Panel>控件可以包含滚动条和仅<xref:System.Windows.Forms.GroupBox>控件显示的标题。  
  
## <a name="key-properties"></a>键属性  
 若要显示滚动条，请设置<xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A>属性设置为`true`。 你还可以通过设置定义面板的外观<xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.BackgroundImage%2A>，和<xref:System.Windows.Forms.Panel.BorderStyle%2A>属性。 有关详细信息<xref:System.Windows.Forms.Control.BackColor%2A>并<xref:System.Windows.Forms.Control.BackgroundImage%2A>属性，请参阅[如何：设置面板的背景](how-to-set-the-background-of-a-windows-forms-panel.md)。 <xref:System.Windows.Forms.Panel.BorderStyle%2A>属性确定是否面板概述了与没有可见的边框 (<xref:System.Windows.Forms.BorderStyle.None>)，普通行 (<xref:System.Windows.Forms.BorderStyle.FixedSingle>)，或隐藏的行 (<xref:System.Windows.Forms.BorderStyle.Fixed3D>)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Panel>
- [GroupBox 控件](groupbox-control-windows-forms.md)
- [如何：通过使用设计器使用 Windows 窗体 Panel 控件对控件进行分组](group-controls-with-wf-panel-control-using-the-designer.md)
- [如何：使用设计器设置 Windows 窗体面板的背景](how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
