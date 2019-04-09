---
title: RadioButton 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: 1210658226d9bcacbf4904fdc90a9908c34f5b73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129111"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton 控件概述（Windows 窗体）
Windows 窗体<xref:System.Windows.Forms.RadioButton>控件向用户显示的一组两个或多个互斥选项。 尽管单选按钮和复选框似乎作用类似，但还有一项重大差异： 如果用户选择的单选按钮，不能同时选中同一个组中的其他单选按钮。 与此相反，可以选择任意数量的复选框。 定义单选按钮组将告诉用户:"这是一组选项，您可以从中选择一个且只有一个。"  
  
## <a name="using-the-control"></a>使用控件  
 当<xref:System.Windows.Forms.RadioButton>单击控件时，其<xref:System.Windows.Forms.RadioButton.Checked%2A>属性设置为`true`和<xref:System.Windows.Forms.Control.Click>调用事件处理程序。 <xref:System.Windows.Forms.RadioButton.CheckedChanged>引发事件时的值<xref:System.Windows.Forms.RadioButton.Checked%2A>属性更改。 如果<xref:System.Windows.Forms.RadioButton.AutoCheck%2A>属性设置为`true`（默认值），选中单选按钮组中的所有其他会自动清除。 此属性通常是仅设置为`false`时使用验证代码，以确保选定的单选按钮都是允许的选项。 在控件中显示的文本设置与<xref:System.Windows.Forms.Control.Text%2A>属性，它可以包含访问键的快捷方式。 访问密钥，用户通过按 ALT 键和访问密钥"单击"控件。 有关详细信息，请参阅[如何：Windows 窗体控件的创建访问键](how-to-create-access-keys-for-windows-forms-controls.md)和[如何：设置显示的文本的 Windows 窗体控件](how-to-set-the-text-displayed-by-a-windows-forms-control.md)。  
  
 <xref:System.Windows.Forms.RadioButton>控件可以显示类似于命令按钮，似乎已按下，如果选择，如果<xref:System.Windows.Forms.RadioButton.Appearance%2A>属性设置为<xref:System.Windows.Forms.Appearance.Button>。 单选按钮还可以显示使用图像<xref:System.Windows.Forms.ButtonBase.Image%2A>和<xref:System.Windows.Forms.ButtonBase.ImageList%2A>属性。 有关详细信息，请参阅[如何：设置所显示的图像的 Windows 窗体控件](how-to-set-the-image-displayed-by-a-windows-forms-control.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.RadioButton>
- [Panel 控件概述](panel-control-overview-windows-forms.md)
- [GroupBox 控件概述](groupbox-control-overview-windows-forms.md)
- [CheckBox 控件概述](checkbox-control-overview-windows-forms.md)
- [如何：创建 Windows 窗体控件的访问键](how-to-create-access-keys-for-windows-forms-controls.md)
- [如何：设置 Windows 窗体控件显示的文本](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [如何：按功能分组 Windows 窗体 RadioButton 控件](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [RadioButton 控件](radiobutton-control-windows-forms.md)
