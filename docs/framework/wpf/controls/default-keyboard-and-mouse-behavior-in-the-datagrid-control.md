---
title: DataGrid 控件中的默认键盘和鼠标行为
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
ms.openlocfilehash: 6be464ce85bd3ba91dd6e6cc810ec7d04edc0c3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083317"
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>DataGrid 控件中的默认键盘和鼠标行为
本主题介绍用户如何与交互<xref:System.Windows.Controls.DataGrid>控件中的使用键盘和鼠标。  
  
 与典型交互<xref:System.Windows.Controls.DataGrid>包括导航、 选择和编辑。 选择行为受<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>和<xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>属性。 本主题中导致所述的行为的默认值是<xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType>和<xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>。 更改这些值可能会导致不同于所述的行为。 编辑控件时单元格处于编辑模式下，可能会重写的标准键盘行为<xref:System.Windows.Controls.DataGrid>。  
  
## <a name="default-keyboard-behavior"></a>默认键盘行为  
 下表列出的默认键盘行为<xref:System.Windows.Controls.DataGrid>。  
  
|键或键组合|描述|  
|----------------------------|-----------------|  
|向下键|将焦点移到当前单元格的正下方的单元格。 如果焦点位于最后一行中，按向下键没有任何影响。|  
|向上键|将焦点移到当前单元格的正上方的单元格。 如果焦点位于第一行中，按向上键没有任何影响。|  
|向左键|将焦点移到上一个单元格的行中。 如果焦点位于行中的第一个单元中，按向左键没有任何影响。|  
|向右键|将焦点移到下一个单元格的行中。 如果焦点位于行中的最后一个单元中，按向右箭头没有任何影响。|  
|Home|将焦点移到当前行中的第一个单元。|  
|End|将焦点移到当前行中的最后一个单元。|  
|Page Down|如果未分组的行，将控件向下滚动完全显示的行数。 将焦点移动到完全显示的最后一行，而无需更改的列。<br /><br /> 如果行分组，将焦点移到中的最后一行<xref:System.Windows.Controls.DataGrid>而无需更改的列。|  
|Page Up|如果未分组的行，该控件向上滚动完全显示的行数。 将焦点移到而无需更改列显示的第一行。<br /><br /> 如果行分组，将焦点移到中的第一行<xref:System.Windows.Controls.DataGrid>而无需更改的列。|  
|Tab|将焦点移到下一个单元格的当前行。 如果焦点位于行的最后一个单元格，则将焦点移到下一行中的第一个单元。 如果焦点在控件中的最后一个单元中，将焦点移到下一个控件的父容器的 tab 键顺序。<br /><br /> 如果当前单元格处于编辑模式并按 tab 键引起焦点将从当前行移开，对行所做的任何更改会提交更改焦点之前。|  
|Shift+Tab|将焦点移到上一个单元格的当前行中。 如果焦点已在行的第一个单元中，将焦点移到上一行中的最后一个单元。 如果焦点在控件中的第一个单元中，将焦点移到上一个控件的父容器的 tab 键顺序。<br /><br /> 如果当前单元格处于编辑模式并按 tab 键引起焦点将从当前行移开，对行所做的任何更改会提交更改焦点之前。|  
|Ctrl+向下键|将焦点移到当前列中的最后一个单元格。|  
|Ctrl+向上键|将焦点移到当前列中的第一个单元格。|  
|Ctrl+向右键|将焦点移到当前行中的最后一个单元。|  
|Ctrl+向左键|将焦点移到当前行中的第一个单元。|  
|CTRL + HOME|将焦点移到控件中的第一个单元。|  
|CTRL + END|将焦点移到控件中的最后一个单元。|  
|Ctrl+Page Down|向下翻页相同。|  
|Ctrl+Page Up|向上翻页相同。|  
|F2|如果<xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType>属性是`false`并<xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType>属性是`false`当前列中，将当前单元格放入单元格编辑模式。|  
|Enter|提交到当前单元格和行的任何更改并将焦点移到当前单元格的正下方的单元格。 如果焦点位于最后一行中，而无需移动焦点提交任何更改。|  
|ESC|如果控件处于编辑模式下，取消编辑，恢复在控件中所做的任何更改。 如果基础数据源实现<xref:System.ComponentModel.IEditableObject>，第二次按 esc 键取消整个行的编辑模式。|  
|退格符|编辑单元格时，请删除光标位置前的字符。|  
|DELETE|编辑单元格时，光标位置后删除的字符。|  
|Ctrl+Enter|而无需将焦点移动到当前单元格提交任何更改。|  
|Ctrl+A|如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>设置为<xref:System.Windows.Controls.DataGridSelectionMode.Extended>，选择中的所有行<xref:System.Windows.Controls.DataGrid>。|  
  
## <a name="selection-keys"></a>选择键  
 如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>属性设置为<xref:System.Windows.Controls.DataGridSelectionMode.Extended>、 导航行为不会更改，但按下 shift 键 （包括 CTRL + SHIFT） 时使用键盘导航将修改多行选择。 导航开始前，该控件将当前行标记为定位行。 导航在按住 SHIFT 的同时，所选内容包括定位行和当前行之间的所有行。  
  
 以下选择键修改多行的选择。  
  
-   Shift+向下键  
  
-   Shift+向上键  
  
-   Shift+Page Down  
  
-   Shift+Page Up  
  
-   Ctrl+Shift+向下键  
  
-   Ctrl+Shift+向上键  
  
-   CTRL + SHIFT + HOME  
  
-   CTRL + SHIFT + END  
  
## <a name="default-mouse-behavior"></a>默认鼠标行为  
 下表列出了默认鼠标行为<xref:System.Windows.Controls.DataGrid>。  
  
|鼠标操作|描述|  
|------------------|-----------------|  
|单击未选定的行|将当前行，并单击的单元格的当前单元格包含被单击的行。|  
|单击当前单元格|当前单元格置于编辑模式。|  
|拖动列标题单元格|如果<xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType>属性是`true`并<xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType>属性是`true`当前列中，移动列，使其可以放入新的位置。|  
|拖动列标题分隔符|如果<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>属性是`true`并<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>属性是`true`当前列中，调整大小的列。|  
|双击列标题分隔符|如果<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>属性是`true`并<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>属性是`true`当前列中，自动大小的列使用<xref:System.Windows.Controls.DataGridLength.Auto%2A>调整大小模式。|  
|单击列标题单元格|如果<xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType>属性是`true`并<xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType>属性是`true`当前列进行排序的列。<br /><br /> 单击已排序的列标题将反转该列的排序方向。<br /><br /> 当单击多个列标题会按顺序单击多个列进行排序时，按下 SHIFT 键。|  
|CTRL + 单击的行|如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>设置为<xref:System.Windows.Controls.DataGridSelectionMode.Extended>，修改非连续多行选择。<br /><br /> 如果已选择的行，则取消选择该行。|  
|按住 SHIFT 的同时单击的行|如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>设置为<xref:System.Windows.Controls.DataGridSelectionMode.Extended>，修改连续多行选择。|  
|单击行组标题|展开或折叠组。|  
|单击左上角的全选按钮 <xref:System.Windows.Controls.DataGrid>|如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>设置为<xref:System.Windows.Controls.DataGridSelectionMode.Extended>，选择中的所有行<xref:System.Windows.Controls.DataGrid>。|  
  
## <a name="mouse-selection"></a>鼠标选择  
 如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>属性设置为<xref:System.Windows.Controls.DataGridSelectionMode.Extended>，在按下 CTRL 或 SHIFT 的同时单击某一行将修改多行选择。  
  
 时按住 CTRL 的同时单击某一行，该行将更改其选择状态，而所有其他行保留其当前选择状态。 这样做可以选择不相邻的行。  
  
 在按住 SHIFT 的同时单击某一行，所选内容将包括当前行和当前行之前单击位置定位行之间的所有行。 随后按下 shift 键的同时单击更改当前行，而不是定位点行。 此方法选择相邻的行的范围。  
  
 CTRL + SHIFT 可以组合以选择相邻的行的非相邻的范围。 若要执行此操作，选择第一个范围，通过使用 SHIFT + 单击前面所述。 选择的行的第一个范围后，使用 CTRL + 单击可在下一步的范围内，选择第一行，然后按 CTRL + SHIFT 的同时单击下一个范围中的最后一行。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>
