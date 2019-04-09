---
title: 如何：实现 CompositeCollection
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 8361c2bfa9c125aeadf0a62ca86af1855e5c3dbc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091156"
---
# <a name="how-to-implement-a-compositecollection"></a>如何：实现 CompositeCollection
## <a name="example"></a>示例  
 下面的示例演示如何使用 <xref:System.Windows.Data.CompositeCollection> 类将多个集合和项显示为一个列表。 在此示例中，`GreekGods` 是 `GreekGod` 自定义对象的一个 <xref:System.Collections.ObjectModel.ObservableCollection%601>。 定义了数据模板以便 `GreekGod` 对象和 `GreekHero` 对象分别以金色和青色作为前景色显示。  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [数据绑定概述](data-binding-overview.md)
- [帮助主题](data-binding-how-to-topics.md)
