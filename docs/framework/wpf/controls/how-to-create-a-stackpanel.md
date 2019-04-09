---
title: 如何：创建 StackPanel
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: bcf6decff2fbc012b5f8b62794f0d7b2cd9f29fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121805"
---
# <a name="how-to-create-a-stackpanel"></a>如何：创建 StackPanel
此示例演示如何创建<xref:System.Windows.Controls.StackPanel>。  
  
## <a name="example"></a>示例  
 一个<xref:System.Windows.Controls.StackPanel>，可在指定的方向堆叠元素。 通过使用属性上定义的<xref:System.Windows.Controls.StackPanel>，内容可以流动竖向，这是默认设置，还是水平。  
  
 下面的示例垂直堆叠五<xref:System.Windows.Controls.TextBlock>控件，每个都有一个不同<xref:System.Windows.Controls.Border>并<xref:System.Windows.Controls.Border.Background%2A>，通过使用<xref:System.Windows.Controls.StackPanel>。 没有指定的子元素<xref:System.Windows.FrameworkElement.Width%2A>拉伸以填充父窗口; 但是，所具有的子元素指定<xref:System.Windows.FrameworkElement.Width%2A>，在窗口中居中。  
  
 在默认的堆叠方向<xref:System.Windows.Controls.StackPanel>是垂直的。 控件中内容流<xref:System.Windows.Controls.StackPanel>，使用<xref:System.Windows.Controls.StackPanel.Orientation%2A>属性。 你可以通过使用控制水平对齐方式<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>属性。  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.StackPanel>
- [面板概述](panels-overview.md)
- [帮助主题](stackpanel-how-to-topics.md)
