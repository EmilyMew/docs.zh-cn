---
title: NumericUpDown 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: 218eb685e546acac76a18450612a1601ab87276b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109871"
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown 控件概述（Windows 窗体）
<xref:System.Windows.Forms.NumericUpDown>控件看起来像一对用户可以单击来调整值的箭头和文本框中的组合。 该控件显示并从固定数字值选项列表中设置的单个数值。 用户可以增加和减少数，通过单击向上和向下箭头，通过按向上和向下箭头键，或通过在控件的文本框部分中键入一个数字。 单击向上箭头键移动到最大值; 数单击向下箭头键移动到最小值数。  
  
 由于具有通用的功能，此控件是显而易见的选择，例如，如果你想要创建音乐播放器应用程序的音量控件。 <xref:System.Windows.Forms.NumericUpDown>许多 Windows 控制面板应用程序中使用控件。  
  
## <a name="key-properties-and-methods"></a>键属性和方法  
 控件的文本框中显示的数字可以是不同的格式，包括十六进制。 有关详细信息，请参阅[如何：设置 Windows 窗体 NumericUpDown 控件的格式](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)。 控件的主要属性包括<xref:System.Windows.Forms.NumericUpDown.Value%2A>， <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> （默认值为 100）， <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> （默认值 0） 和<xref:System.Windows.Forms.NumericUpDown.Increment%2A>（默认值为 1）。 <xref:System.Windows.Forms.NumericUpDown.Value%2A>属性设置在控件中选定的当前数目。 <xref:System.Windows.Forms.NumericUpDown.Increment%2A>属性设置数字的调整，当用户单击向上或向下箭头。 时焦点移出该控件，将根据该最小值和最大的数字值验证键入的输入。 可以增加该控件在用户连续按向上或向下箭头，在数字上移动的速度与<xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>属性。 控件的主要方法是<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>和<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown 控件](numericupdown-control-windows-forms.md)
- [如何：设置 Windows 窗体 NumericUpDown 控件的格式](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [TextBox 控件](textbox-control-windows-forms.md)
