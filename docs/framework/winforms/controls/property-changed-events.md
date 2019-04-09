---
title: 属性更改事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
ms.openlocfilehash: cabfd9e799288a332a0b2f96140f5f1cc328508b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105763"
---
# <a name="property-changed-events"></a>属性更改事件
如果您希望控件名为的属性时发送通知*PropertyName*的更改，定义一个名为*PropertyName* `Changed`和一个名为方法`On` *PropertyName* `Changed`引发事件。 在 Windows 窗体中的命名约定是追加单词*Changed*到属性的名称。 属性更改事件的关联的事件委托类型是<xref:System.EventHandler>，并且事件数据类型为<xref:System.EventArgs>。 类的基类<xref:System.Windows.Forms.Control>定义多个属性更改事件，例如<xref:System.Windows.Forms.Control.BackColorChanged>， <xref:System.Windows.Forms.Control.BackgroundImageChanged>， <xref:System.Windows.Forms.Control.FontChanged>， <xref:System.Windows.Forms.Control.LocationChanged>，等等。 有关事件的背景信息，请参阅[事件](../../../standard/events/index.md)并[Windows 窗体控件中的事件](events-in-windows-forms-controls.md)。  
  
 属性更改事件非常有用，因为它们允许使用者控件的附加事件处理程序对更改做出响应。 如果您的控件需要以响应，它会发出属性更改事件，重写相应`On` *PropertyName* `Changed`而不是将委托附加到该事件的方法。 通过更新其他属性或重新绘制的部分或所有其绘图图面，控件通常响应属性更改事件。  
  
 下面的示例演示如何`FlashTrackBar`自定义控件对一些它所继承的属性更改事件的响应<xref:System.Windows.Forms.Control>。 有关完整示例，请参阅[如何：创建显示进度的 Windows 窗体控件](how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>请参阅

- [事件](../../../standard/events/index.md)
- [Windows 窗体控件中的事件](events-in-windows-forms-controls.md)
- [Windows 窗体控件中的属性](properties-in-windows-forms-controls.md)
