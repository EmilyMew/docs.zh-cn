---
title: 如何：将主-详细模式与分层 XML 数据结合使用
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: ba6c932f519ffa5c3c70ecb21eb9b5d08c40fb28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086255"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>如何：将主-详细模式与分层 XML 数据结合使用
此示例演示如何使用 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 数据实现主 - 从方案。  
  
## <a name="example"></a>示例  
 此示例是[对分层数据使用主-从模式](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)中讨论的示例的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 版本。 在此示例中，数据来自文件 `League.xml`。 请注意第三个 <xref:System.Windows.Controls.ListBox> 控件如何通过绑定到 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 属性来跟踪第二个 <xref:System.Windows.Controls.ListBox> 中的选择变化。  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.HierarchicalDataTemplate>
- [帮助主题](data-binding-how-to-topics.md)
