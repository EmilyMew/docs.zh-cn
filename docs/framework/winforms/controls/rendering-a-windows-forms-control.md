---
title: 呈现 Windows 窗体控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- OnPaintBackground method [Windows Forms], invoking in Windows Forms custom controls
- custom controls [Windows Forms], graphics resources
- custom controls [Windows Forms], invalidation and painting
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
ms.openlocfilehash: 8de87e17d1baedccfe18bfded3ccab7ab59f0a09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125679"
---
# <a name="rendering-a-windows-forms-control"></a>呈现 Windows 窗体控件
呈现是指创建用户的屏幕上的可视表示形式的过程。 Windows 窗体使用[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]（是的新 Windows 图形库） 以进行呈现。 提供访问权限的托管的类[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]位于<xref:System.Drawing?displayProperty=nameWithType>命名空间及其子命名空间。  
  
 控件呈现中包括以下元素：  
  
-   提供由基类的绘图功能<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。  
  
-   基本元素[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]图形库。  
  
-   几何图形的绘图区域。  
  
-   用于释放图形资源的过程。  
  
## <a name="drawing-functionality-provided-by-control"></a>绘图控件提供的功能  
 类的基类<xref:System.Windows.Forms.Control>提供了绘图功能通过其<xref:System.Windows.Forms.Control.Paint>事件。 中的控件引发<xref:System.Windows.Forms.Control.Paint>事件时需要更新其显示。 有关.NET Framework 中的事件的详细信息，请参阅[处理和引发事件](../../../standard/events/index.md)。  
  
 事件数据类<xref:System.Windows.Forms.Control.Paint>事件， <xref:System.Windows.Forms.PaintEventArgs>，包含所需的绘制控件的数据-图形对象以及表示要在中绘制的区域的矩形对象的句柄。 中显示这些对象中的以下代码片段以粗体显示。  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   Implements IDisposable  
  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property  
   ' Other properties and methods.  
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs, IDisposable {  
public System.Drawing.Rectangle ClipRectangle {get;}  
public System.Drawing.Graphics Graphics {get;}  
// Other properties and methods.  
...  
}  
```  
  
 <xref:System.Drawing.Graphics> 为托管的类封装绘制功能的讨论中所述[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]本主题中更高版本。 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>的一个实例<xref:System.Drawing.Rectangle>结构，并定义可以在其中绘制控件的可用区域。 控件开发人员可以计算<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>使用<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>控件，如本主题后面的几何图形的讨论中所述的属性。  
  
 控件必须提供呈现逻辑通过重写<xref:System.Windows.Forms.Control.OnPaint%2A>方法，它继承自<xref:System.Windows.Forms.Control>。 <xref:System.Windows.Forms.Control.OnPaint%2A> 获取的访问权限的图形对象并通过在中绘制一个矩形<xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A>并<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>的属性<xref:System.Windows.Forms.PaintEventArgs>实例传递给它。  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>方法的基<xref:System.Windows.Forms.Control>类不实现任何绘图功能，但只是调用已注册的事件委托<xref:System.Windows.Forms.Control.Paint>事件。 当您重写<xref:System.Windows.Forms.Control.OnPaint%2A>，通常应调用<xref:System.Windows.Forms.Control.OnPaint%2A>基类以便注册的委托的方法接收<xref:System.Windows.Forms.Control.Paint>事件。 但是，其整个图面绘制的控件不应调用基类的<xref:System.Windows.Forms.Control.OnPaint%2A>，因为这就引入了闪烁。 有关重写的示例<xref:System.Windows.Forms.Control.OnPaint%2A>事件，请参阅[如何：创建显示进度的 Windows 窗体控件](how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
> [!NOTE]
>  不要调用<xref:System.Windows.Forms.Control.OnPaint%2A>直接从您的控件; 相反，调用<xref:System.Windows.Forms.Control.Invalidate%2A>方法 (继承自<xref:System.Windows.Forms.Control>) 或其他方法调用<xref:System.Windows.Forms.Control.Invalidate%2A>。 <xref:System.Windows.Forms.Control.Invalidate%2A>方法又调用<xref:System.Windows.Forms.Control.OnPaint%2A>。 <xref:System.Windows.Forms.Control.Invalidate%2A>方法重载，并根据自变量提供给<xref:System.Windows.Forms.Control.Invalidate%2A> `e`，控件将重绘其部分或全部其屏幕区域。  
  
 基<xref:System.Windows.Forms.Control>类定义可用于绘图的另一种方法 —<xref:System.Windows.Forms.Control.OnPaintBackground%2A>方法。  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 绘制背景 (并因此形状) 的窗口和保证可快速完成，而<xref:System.Windows.Forms.Control.OnPaint%2A>绘制详细信息和可能是较慢，因为单个的绘制请求合并成一个<xref:System.Windows.Forms.Control.Paint>介绍了需要的所有区域的事件重绘。 你可能想要调用<xref:System.Windows.Forms.Control.OnPaintBackground%2A>如果，例如，想要绘制控件的颜色渐变背景。  
  
 虽然<xref:System.Windows.Forms.Control.OnPaintBackground%2A>具有类似于事件的命名法并采用相同参数作为`OnPaint`方法，<xref:System.Windows.Forms.Control.OnPaintBackground%2A>并不是真正的事件方法。 没有任何`PaintBackground`事件和<xref:System.Windows.Forms.Control.OnPaintBackground%2A>不会调用事件委托。 重写时<xref:System.Windows.Forms.Control.OnPaintBackground%2A>方法，派生的类不需要调用<xref:System.Windows.Forms.Control.OnPaintBackground%2A>其基类的方法。  
  
## <a name="gdi-basics"></a>GDI + 基础知识  
 <xref:System.Drawing.Graphics>类提供绘制各种形状，如圆圈、 三角形、 弧线和椭圆的方法，以及用于显示文本的方法。 <xref:System.Drawing?displayProperty=nameWithType>命名空间和及其子命名空间包含类封装图形元素，如 （圆圈、 矩形、 弧线和其他人） 的形状、 颜色、 字体、 画笔和等等。 有关详细信息[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]，请参阅[使用托管图形类](../advanced/using-managed-graphics-classes.md)。 基础知识[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]中也描述了[如何：创建显示进度的 Windows 窗体控件](how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
## <a name="geometry-of-the-drawing-region"></a>几何图形的绘图区域  
 <xref:System.Windows.Forms.Control.ClientRectangle%2A>控件的属性指定可用于在用户的屏幕上，控件的矩形区域时<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>属性的<xref:System.Windows.Forms.PaintEventArgs>指定实际绘制的区域。 (请记住，完成绘制<xref:System.Windows.Forms.Control.Paint>采用的事件方法<xref:System.Windows.Forms.PaintEventArgs>实例作为其参数)。 控件可能需要绘制只有其可用区域中，部分因为是控件的显示更改这种情况时一小部分。 在这些情况下，控件开发人员必须计算实际的矩形中绘制，并将其传递给<xref:System.Windows.Forms.Control.Invalidate%2A>。 重载的版本<xref:System.Windows.Forms.Control.Invalidate%2A>采用<xref:System.Drawing.Rectangle>或<xref:System.Drawing.Region>作为参数使用该参数生成<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>属性<xref:System.Windows.Forms.PaintEventArgs>。  
  
 以下代码段显示了`FlashTrackBar`自定义控件计算绘制的矩形区域。 `client`变量表示<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>属性。 有关完整示例，请参阅[如何：创建显示进度的 Windows 窗体控件](how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>释放图形资源  
 图形对象非常昂贵，因为它们使用的系统资源。 此类对象包含的实例<xref:System.Drawing.Graphics?displayProperty=nameWithType>类的实例以及<xref:System.Drawing.Brush?displayProperty=nameWithType>， <xref:System.Drawing.Pen?displayProperty=nameWithType>，和其他图形类。 仅当需要它并将其释放时创建的图形资源很重要很快完成后使用它。 如果您创建的类型实现<xref:System.IDisposable>接口中，调用其<xref:System.IDisposable.Dispose%2A>方法完成后使用它来释放资源。  
  
 以下代码段显示如何`FlashTrackBar`自定义控件创建和释放<xref:System.Drawing.Brush>资源。 有关完整的源代码，请参阅[如何：创建显示进度的 Windows 窗体控件](how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>请参阅

- [如何：创建显示进度的 Windows 窗体控件](how-to-create-a-windows-forms-control-that-shows-progress.md)
