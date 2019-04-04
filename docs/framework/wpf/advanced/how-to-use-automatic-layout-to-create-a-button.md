---
title: 如何：使用自动布局创建按钮
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 8eb1e93dd87c210812c9b7758c744a616ef2d862
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409778"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>如何：使用自动布局创建按钮
本示例介绍如何使用自动布局方法在可本地化的应用程序中创建按钮。  
  
 本地化[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]是一个耗时的过程。 通常，本地化人员除翻译文本外，还需要重新调整元素大小并重新定位元素。 在过去每种语言的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]改编需要进行调整。 现在使用的功能[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]可以设计减少必需的调整的元素。 种编写可以更轻松地重设大小和重新定位应用程序的方法称为`automatic layout`。  
  
## <a name="example"></a>示例  

以下两个[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]示例创建的应用程序实例化按钮; 一个使用英文文本，另一个使用西班牙文本。 请注意，除文本之外，代码都一样；按钮会配合文字进行调整。

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 下图显示了与自动调整大小的按钮的代码示例的输出：
  
 ![具有不同语言的文本的同一按钮](./media/use-automatic-layout-overview/auto-resizable-button.png)  
  
## <a name="see-also"></a>请参阅

- [使用自动布局概述](use-automatic-layout-overview.md)
- [使用网格进行自动布局](how-to-use-a-grid-for-automatic-layout.md)
