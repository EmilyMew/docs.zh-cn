---
title: 重写 OnPaint 方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
ms.openlocfilehash: baf4e6cb3b2a40b1b792ae12e78cb9f878a738ff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124301"
---
# <a name="overriding-the-onpaint-method"></a>重写 OnPaint 方法
重写中定义任何事件的基本步骤[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]相同，并且在以下列表总结了。  
  
#### <a name="to-override-an-inherited-event"></a>若要重写继承的事件  
  
1.  重写受保护`On` *EventName*方法。  
  
2.  调用`On` *EventName*方法重写从基类`On` *EventName*方法，因此已注册的委托接收事件。  
  
 <xref:System.Windows.Forms.Control.Paint>在此处详细论述事件，因为每个 Windows 窗体控件必须重写<xref:System.Windows.Forms.Control.Paint>它所继承的事件<xref:System.Windows.Forms.Control>。 基<xref:System.Windows.Forms.Control>类不知道如何派生的控件需要绘制时，它不提供任何绘制逻辑中的<xref:System.Windows.Forms.Control.OnPaint%2A>方法。 <xref:System.Windows.Forms.Control.OnPaint%2A>方法<xref:System.Windows.Forms.Control>只需将调度<xref:System.Windows.Forms.Control.Paint>到已注册的事件接收器的事件。  
  
 如果您已完成中的示例[如何：开发简单的 Windows 窗体控件](how-to-develop-a-simple-windows-forms-control.md)，你已了解的重写示例<xref:System.Windows.Forms.Control.OnPaint%2A>方法。 下面的代码片段摘自该示例。  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control {  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <xref:System.Windows.Forms.PaintEventArgs>类包含用于数据<xref:System.Windows.Forms.Control.Paint>事件。 它具有两个属性，如下面的代码中所示。  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 是否要绘制的矩形和<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A>属性是指<xref:System.Drawing.Graphics>对象。 中的类<xref:System.Drawing?displayProperty=nameWithType>管理命名空间提供的功能的访问的类[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，新的 Windows 图形库。 <xref:System.Drawing.Graphics>对象具有用于绘制点、 字符串、 线条、 弧线、 椭圆和许多其他形状的方法。  
  
 控件调用其<xref:System.Windows.Forms.Control.OnPaint%2A>方法需要更改其可视显示时。 此方法反过来引发<xref:System.Windows.Forms.Control.Paint>事件。  
  
## <a name="see-also"></a>请参阅

- [事件](../../../standard/events/index.md)
- [呈现 Windows 窗体控件](rendering-a-windows-forms-control.md)
- [定义事件](defining-an-event-in-windows-forms-controls.md)
