---
title: 如何：使用填充在 Windows 窗体控件周围创建边框
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins
- controls [Windows Forms], Margin property
- padding [Windows Forms], Windows Forms
- controls [Windows Forms], Padding property
- controls [Windows Forms], outlining
- Padding property [Windows Forms]
- margins [Windows Forms], Windows Forms
- Margin property [Windows Forms]
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
ms.openlocfilehash: e3bbf43dbe45e675df172a6c3e1db16a3ba9caa8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124016"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>如何：使用填充在 Windows 窗体控件周围创建边框
下面的代码示例演示如何创建一个边框或周围的轮廓<xref:System.Windows.Forms.RichTextBox>控件。 该示例设置的值<xref:System.Windows.Forms.Panel>控件的<xref:System.Windows.Forms.Padding>属性设置为 5 和集<xref:System.Windows.Forms.Control.Dock%2A>的子属性<xref:System.Windows.Forms.RichTextBox>控制对<xref:System.Windows.Forms.DockStyle.Fill>。 <xref:System.Windows.Forms.Control.BackColor%2A>的<xref:System.Windows.Forms.Panel>控件设置为<xref:System.Drawing.Color.Blue%2A>，这将创建周围的蓝色边框<xref:System.Windows.Forms.RichTextBox>控件。  
  
## <a name="example"></a>示例  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Padding>
- [Windows 窗体控件中的边距和填充](margin-and-padding-in-windows-forms-controls.md)
