---
title: 如何：更改 Windows 窗体 ColorDialog 组件的外观
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: d79139ac3d11d3cd9a7d1bbe1f12e14df83530e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094640"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>如何：更改 Windows 窗体 ColorDialog 组件的外观
你可以配置 Windows 窗体外观<xref:System.Windows.Forms.ColorDialog>组件与多个其属性。 该对话框具有两个部分 — 一个显示基本颜色，另一部分允许用户定义的自定义颜色。  
  
 大部分属性限制哪些用户可以从对话框中选择的颜色。 如果<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>属性设置为`true`，允许用户定义自定义颜色。 <xref:System.Windows.Forms.ColorDialog.FullOpen%2A>属性是`true`如果对话框中展开定义自定义颜色; 通过否则用户必须单击"定义自定义颜色"按钮。 当<xref:System.Windows.Forms.ColorDialog.AnyColor%2A>属性设置为`true`，对话框显示基本颜色集中可用的所有颜色。 如果<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>属性设置为`true`，用户不能选择抖色的颜色; 仅纯色可供选择。  
  
 如果<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>属性设置为`true`，帮助按钮显示在对话框中。 当用户单击帮助按钮<xref:System.Windows.Forms.ColorDialog>组件的<xref:System.Windows.Forms.CommonDialog.HelpRequest>引发事件。  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>若要配置的颜色对话框外观  
  
1.  设置<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>， <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>， <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>，和<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>属性设置为所需的值。  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog 组件](colordialog-component-windows-forms.md)
- [ColorDialog 组件概述](colordialog-component-overview-windows-forms.md)
