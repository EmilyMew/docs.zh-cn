---
title: LinkLabel 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 541467b0f1285d372e5f6d502d9d8f28c8c6333e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083122"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel 控件概述（Windows 窗体）
Windows 窗体<xref:System.Windows.Forms.LinkLabel>让您可以将 Web 样式的链接添加到 Windows 窗体应用程序。 可以使用<xref:System.Windows.Forms.LinkLabel>包括可以使用的内容控件<xref:System.Windows.Forms.Label>控制; 还可以设置为文件、 文件夹或 Web 页的链接的文本的一部分。  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>可以使用 LinkLabel 控件执行的操作  
 除了所有属性、 方法和事件<xref:System.Windows.Forms.Label>控件，<xref:System.Windows.Forms.LinkLabel>控件具有超链接和链接颜色的属性。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>属性设置的激活链接的文本的区域。 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>， <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>，和<xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A>属性设置的链接的颜色。 <xref:System.Windows.Forms.LinkLabel.LinkClicked>事件确定链接文本选择时，会发生什么情况。  
  
 最简单用法<xref:System.Windows.Forms.LinkLabel>控件将显示一个链接使用<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>属性，但您还可以显示多个超链接使用<xref:System.Windows.Forms.LinkLabel.Links%2A>属性。 <xref:System.Windows.Forms.LinkLabel.Links%2A>属性使您能够访问链接的集合。 此外可以指定中的数据<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>属性的每个单独<xref:System.Windows.Forms.LinkLabel.Link>对象。 值<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>属性可以用于存储要显示的文件的位置或 Web 站点的地址。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.LinkLabel>
- [Label 控件概述](label-control-overview-windows-forms.md)
- [如何：使用 Windows 窗体 LinkLabel 控件链接到对象或 Web 页面](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [如何：更改 Windows 窗体 LinkLabel 控件的外观](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
