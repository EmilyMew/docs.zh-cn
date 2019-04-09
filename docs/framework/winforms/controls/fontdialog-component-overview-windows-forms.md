---
title: FontDialog 组件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 7f140807bf4b42e530302190042e729c59248e7f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098554"
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog 组件概述（Windows 窗体）
Windows 窗体<xref:System.Windows.Forms.FontDialog>组件是一个预配置的对话框，这是标准的 Windows**字体**用于公开当前系统安装的字体的对话框。 将其作为一个简单的解决方案在基于 Windows 的应用程序中的字体选择而不用配置你自己的对话框。  
  
 默认情况下，该对话框显示列表框的字体的字体样式和大小;效果复选框，如带删除线和下划线;脚本; 下拉列表和字体的显示方式的示例。 （脚本将引用不同的字符脚本可用于给定的字体，例如，希伯来语或日语。）若要显示字体对话框中，调用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。  
  
## <a name="key-properties"></a>键属性  
 该组件具有多个配置其外观的属性。 将对话框中选择设置的属性是<xref:System.Windows.Forms.FontDialog.Font%2A>和<xref:System.Windows.Forms.FontDialog.Color%2A>。 <xref:System.Windows.Forms.FontDialog.Font%2A>属性设置字体、 样式、 大小、 脚本和效果; 例如， `Arial, 10pt, style=Italic, Strikeout`。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.FontDialog>
- [FontDialog 组件](fontdialog-component-windows-forms.md)
