---
title: Windows 窗体坐标
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: 6feabadff17538f4a7368c348f7b72226e2d678e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116126"
---
# <a name="windows-forms-coordinates"></a>Windows 窗体坐标
Windows 窗体坐标系统取决于设备坐标，并在 Windows 窗体中绘制时的度量值的基本单位是将设备单位 （通常情况下，像素）。 在屏幕上的点的 x 坐标和 y 坐标对所述增加到右侧和 y 坐标增加从上到下的 x 坐标。 原点，相对于屏幕的位置不定，具体取决于是否要指定屏幕或客户端坐标。  
  
## <a name="screen-coordinates"></a>屏幕坐标  
 Windows 窗体应用程序在屏幕坐标中屏幕上指定窗口的位置。 对于屏幕坐标原点是屏幕的左上角。 窗口的完整位置通常描述由<xref:System.Drawing.Rectangle>结构，它包含两个点定义窗口的左上角和右下角的屏幕坐标。  
  
## <a name="client-coordinates"></a>客户端坐标  
 Windows 窗体应用程序窗体或控件使用客户端坐标中指定点的位置。 工作区坐标中的源是控件或窗体的工作区的左上角。 客户端坐标可确保在应用程序可以在窗体或控件，而不考虑屏幕上的控件的窗体的位置绘制时使用一致的坐标值。  
  
 客户端区域的尺寸，还介绍了通过<xref:System.Drawing.Rectangle>结构，其中包含工作区坐标中的区域。 在所有情况下，该矩形的左上角坐标包含工作区中，而排除右下角坐标。 图形操作不包括的工作区上边缘右和下边缘。 例如<xref:System.Drawing.Graphics.FillRectangle%2A>方法将被填满到指定的矩形中，右和下边缘，但不是会包括这些边缘。  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>从一种类型的坐标映射到另一个  
 有时，可能需要从屏幕坐标映射到客户端坐标。 您可以轻松地实现此目的通过使用<xref:System.Windows.Forms.Control.PointToClient%2A>并<xref:System.Windows.Forms.Control.PointToScreen%2A>方法中提供<xref:System.Windows.Forms.Control>类。 例如，<xref:System.Windows.Forms.Control.MousePosition%2A>属性的<xref:System.Windows.Forms.Control>屏幕坐标中报告但你可能想要将它们转换成工作区坐标中。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
