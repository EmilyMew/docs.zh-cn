---
title: 表概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: 4abb6368946f9dac5fdefd6ca44f3adeed55f78f
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410809"
---
# <a name="table-overview"></a>表概述
<xref:System.Windows.Documents.Table> 为支持流文档内容的基于网格的表示形式的块级别元素。 此元素极具灵活性，因此很有用，但也因此显得更加复杂，从而不容易理解和正确使用。  
  
 本主题包含以下各节：  
  
-   [表基础](#table_basics)  
  
-   [表与网格有什么区别？](#table_vs_Grid)  
  
-   [基本表结构](#basic_table_structure)  
  
-   [表包含](#table_containment)  
  
-   [行分组](#row_groupings)  
  
-   [背景呈现优先级](#rendering_precedence)  
  
-   [跨行或列 ](#spanning_rows_or_columns)  
  
-   [使用代码生成表 ](#building_a_table_with_code)  
  
-   [相关主题] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>表基础  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>表与网格有什么区别？  
 <xref:System.Windows.Documents.Table> 和<xref:System.Windows.Controls.Grid>共享某些通用功能，但每个都是最适用于不同的方案。 一个<xref:System.Windows.Documents.Table>专为流内容内使用 (请参阅[流文档概述](flow-document-overview.md)有关流内容的详细信息)。 网格最适合在表单内（主要在流内容以外的任意位置）使用。 内<xref:System.Windows.Documents.FlowDocument>，<xref:System.Windows.Documents.Table>支持流内容行为，如分页、 列重排和内容时选择<xref:System.Windows.Controls.Grid>却没有。 一个<xref:System.Windows.Controls.Grid>另一方面最好使用之外<xref:System.Windows.Documents.FlowDocument>包括的原因有很多<xref:System.Windows.Controls.Grid>根据行和列索引添加元素<xref:System.Windows.Documents.Table>却没有。 <xref:System.Windows.Controls.Grid>元素可对子内容，从而允许多个元素共存于单个"单元格。"内进行分层 <xref:System.Windows.Documents.Table> 不支持分层。 子元素的<xref:System.Windows.Controls.Grid>相对于其"单元格"边界区域进行绝对定位。 <xref:System.Windows.Documents.Table> 不支持此功能。 最后，<xref:System.Windows.Controls.Grid>需要较少的资源，然后<xref:System.Windows.Documents.Table>因此请考虑使用<xref:System.Windows.Controls.Grid>以提高性能。  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>基本表结构  
 <xref:System.Windows.Documents.Table> 提供基于网格的表示形式，包括列 (由<xref:System.Windows.Documents.TableColumn>元素) 和行 (由<xref:System.Windows.Documents.TableRow>元素)。 <xref:System.Windows.Documents.TableColumn> 元素不承载的内容;它们只需定义列和列的特征。 <xref:System.Windows.Documents.TableRow> 元素必须承载于<xref:System.Windows.Documents.TableRowGroup>元素，它定义的表中行的分组。 <xref:System.Windows.Documents.TableCell> 元素，其中包含要显示的表的实际内容，必须承载于<xref:System.Windows.Documents.TableRow>元素。 <xref:System.Windows.Documents.TableCell> 只能包含派生的元素<xref:System.Windows.Documents.Block>。  有效子元素<xref:System.Windows.Documents.TableCell>包括。  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell> 元素不能直接承载文本内容。 有关流的包含规则的详细信息之类的内容元素<xref:System.Windows.Documents.TableCell>，请参阅[流文档概述](flow-document-overview.md)。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> 类似于<xref:System.Windows.Controls.Grid>元素但具有更多功能，因此，需要更大的资源开销。  
  
 下面的示例定义一个简单的 2 x 3 个表与[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]。  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 下图显示了此示例的呈现效果。  
  
 ![屏幕截图显示了一个基本表的呈现效果。](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>表包容  
 <xref:System.Windows.Documents.Table> 派生自<xref:System.Windows.Documents.Block>元素，并遵循的常见规则<xref:System.Windows.Documents.Block>级别元素。  一个<xref:System.Windows.Documents.Table>元素可包含任何以下元素：  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>行分组  
 <xref:System.Windows.Documents.TableRowGroup>元素提供任意表中的组行的方式; 表中的每一行必须属于一个行分组。  行分组中的行通常具有相同的用途，并可作为一个组来设置样式。  行分组的一个常见使用方式是用于将特定用途的行（如标题行、标头和页脚行）与表中所含的主内容分隔开来。  
  
 下面的示例使用[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]定义具有带样式的页眉和页脚行的表。  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 下图显示了此示例的呈现效果。  
  
 ![屏幕快照：表行进行分组](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>背景呈现优先级  
 表元素以下列顺序呈现（按 Z 顺序从最低到最高排列）。 此顺序不能更改。 例如，对于这些元素，没有可用于替换此已有顺序的“Z 顺序”属性。  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 请参考以下示例，该示例对表内每个元素的背景色进行定义。  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 下图显示了此示例的呈现方式（仅显示背景色）。  
  
 ![屏幕快照：表 z&#45;顺序](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>跨行或列  
 表格单元格可能配置为使用跨越多个行或列<xref:System.Windows.Documents.TableCell.RowSpan%2A>或<xref:System.Windows.Documents.TableCell.ColumnSpan%2A>特性分别。  
  
 请参考以下示例，该示例中有一个跨三列的单元格。  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 下图显示了此示例的呈现效果。  
  
 ![屏幕快照：跨全部三列的单元格](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>使用代码生成表  
 以下示例演示如何以编程方式创建<xref:System.Windows.Documents.Table>并填充其内容。 表的内容被分为五个行 (由<xref:System.Windows.Documents.TableRow>中所含对象<xref:System.Windows.Documents.Table.RowGroups%2A>对象) 和六列 (由<xref:System.Windows.Documents.TableColumn>对象)。 各行用于不同的显示目的，其中，标题行用于显示整个表的标题，标头行用于描述表中的数据列，而页脚行则包含摘要信息。  请注意，“标题”行、“标头”行和“页脚”行并非表格所固有的，它们只是具有不同特征的行。 表单元格包含实际内容，可以包含文本、 图像或几乎任何其他[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]元素。  
  
 首先，<xref:System.Windows.Documents.FlowDocument>创建到主机<xref:System.Windows.Documents.Table>，和一个新<xref:System.Windows.Documents.Table>被创建并添加到的内容<xref:System.Windows.Documents.FlowDocument>。  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 下一步，六<xref:System.Windows.Documents.TableColumn>创建对象，并添加到表的<xref:System.Windows.Documents.Table.Columns%2A>集合中的，同时应用某些格式设置。  
  
> [!NOTE]
>  请注意，表的<xref:System.Windows.Documents.Table.Columns%2A>集合使用标准的从零开始索引。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 接下来，创建一个标题行，并将其添加到表中，同时应用某些格式设置。  标题行包含一个单元格，该单元格跨表中的全部六列。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 接下来，创建一个标头行并将其添加到表中，同时创建标头行中的单元格并填充其内容。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 接下来，创建一个数据行并将其添加到表中，同时创建此行中的单元格并填充其内容。  生成此行的过程与生成标头行的过程类似，只是应用的格式设置略有不同。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 最后，创建、添加脚注行并设置其格式。  与标题行类似，脚注包含的单元格的跨度为表中的全部六列。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>请参阅
- [流文档概述](flow-document-overview.md)
- [使用 XAML 定义表](how-to-define-a-table-with-xaml.md)
- [WPF 中的文档](documents-in-wpf.md)
- [使用流内容元素](how-to-use-flow-content-elements.md)
