---
title: 如何：对分层数据使用主-从模式
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: e18bc7d60b47b083a0b102938634473d85b39882
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463314"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>如何：对分层数据使用主-从模式
此示例演示如何实现母版-详细信息方案。  
  
## <a name="example"></a>示例  
 在此示例中，`LeagueList` 是 `Leagues` 的集合。 每个 `League` 有一个 `Name` 和一个 `Divisions` 的集合，每个 `Division` 有一个名称和一个 `Teams` 的集合。 每个 `Team` 有一个团队名称。  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 下面是该示例的一个屏幕快照。 `Divisions` 列表框<xref:System.Windows.Controls.ListBox>自动跟踪 `Leagues` 列表框<xref:System.Windows.Controls.ListBox>中的选择并显示相应的数据。 `Teams` 列表框<xref:System.Windows.Controls.ListBox>跟踪其他两个列表框<xref:System.Windows.Controls.ListBox>控件中的选择。  
  
 ![显示一个母版的屏幕截图&#45;详细信息方案示例。](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 在此示例中，有两点需要注意：  
  
1.  这三个 <xref:System.Windows.Controls.ListBox> 控件绑定到相同的源。 需设置绑定的 <xref:System.Windows.Data.Binding.Path%2A> 属性，用于指定 <xref:System.Windows.Controls.ListBox> 显示哪个级别的数据。  
  
2.  对于要跟踪其选择内容的 <xref:System.Windows.Controls.ListBox> 控件, 须将其 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> 属性设置为 `true`。 设置此属性可确保所选的项始终设置为 <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。 或者，如果 <xref:System.Windows.Controls.ListBox> 从 <xref:System.Windows.Data.CollectionViewSource> 获取数据，它会自动同步所选内容和货币。  
  
 使用[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]数据时，采用的方法略有不同。 有关示例，请参阅[对分层 XML 数据使用主-从模式](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.HierarchicalDataTemplate>
- [绑定到集合并根据选择的内容显示信息](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [数据绑定概述](data-binding-overview.md)
- [数据模板化概述](data-templating-overview.md)
- [帮助主题](data-binding-how-to-topics.md)
