---
title: DomainUpDown 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: bfe3e7239f77c6f1a0d9bb46a96c704653b43364
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102851"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown 控件概述（Windows 窗体）
Windows 窗体<xref:System.Windows.Forms.DomainUpDown>控件是一对用于列表中向上或向下移动按钮和实质上是组合的文本框。 该控件显示并从选项列表中设置一个文本字符串。 用户可以选择字符串，通过单击向上和向下按钮以浏览列表中，通过按向上和向下箭头键，或通过键入与匹配列表中的项的字符串。 此控件的可能用途之一是从名称按字母顺序排序列表中选择项。  
  
> [!NOTE]
>  若要对列表进行排序，设置<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>属性设置为`true`。  
  
 此控件的功能是非常类似于列表框或组合框中，但其占用空间很少。  
  
## <a name="key-properties"></a>键属性  
 控件的主要属性包括<xref:System.Windows.Forms.DomainUpDown.Items%2A>， <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>，和<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。 <xref:System.Windows.Forms.DomainUpDown.Items%2A>属性包含的控件中显示其文本值的对象的列表。 如果<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>设置为`false`，该控件自动完成用户类型，并为列表中的值匹配的文本。 如果<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>设置为`true`，滚过最后一项将转到第一个项列表中，反之亦然。 控件的主要方法是<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>和<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。  
  
 此控件只显示文本字符串。 如果你想显示的数字值的控件，使用<xref:System.Windows.Forms.NumericUpDown>控件。 有关详细信息，请参阅[NumericUpDown 控件概述](numericupdown-control-overview-windows-forms.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown 控件](domainupdown-control-windows-forms.md)
