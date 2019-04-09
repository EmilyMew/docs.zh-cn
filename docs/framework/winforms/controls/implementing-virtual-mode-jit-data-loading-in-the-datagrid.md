---
title: 在 Windows 窗体 DataGridView 控件中实现实时数据加载的虚拟模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
ms.openlocfilehash: 641db19cc6493a20c9f9a34622f466e3623c32ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088647"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>在 Windows 窗体 DataGridView 控件中实现实时数据加载的虚拟模式
实现中的虚拟模式的一个原因<xref:System.Windows.Forms.DataGridView>控件是仅在需要时检索数据。 这称为*中实时数据加载*。  
  
 如果您正在使用远程数据库中的大型表，例如，您可能希望避免通过检索数据所需的显示和检索其他数据，仅当用户滚动到视图中新行时启动延迟。 如果运行你的应用程序的客户端计算机具有有限的数量的内存可用于存储数据，可能想要从数据库检索新值时放弃未使用的数据。  
  
 以下部分介绍如何使用<xref:System.Windows.Forms.DataGridView>中实时缓存使用的控件。  
  
 要将本主题中的代码作为单个列表进行复制，请参阅[如何：实现虚拟模式在 Windows 中实时数据加载窗体 DataGridView 控件](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。  
  
## <a name="the-form"></a>在窗体  
 下面的代码示例定义一个包含一个只读的窗体<xref:System.Windows.Forms.DataGridView>与交互的控件`Cache`对象，通过<xref:System.Windows.Forms.DataGridView.CellValueNeeded>事件处理程序。 `Cache`对象管理的本地存储的值，并使用`DataRetriever`要从 Northwind 示例数据库的订单表中检索值对象。 `DataRetriever`对象，用于实现`IDataPageRetriever`所需的接口`Cache`类中，还用来初始化<xref:System.Windows.Forms.DataGridView>控制行和列。  
  
 `IDataPageRetriever`， `DataRetriever`，和`Cache`更高版本中本主题介绍了类型。  
  
> [!NOTE]
>  将敏感信息（如密码）存储在连接字符串中可能会影响应用程序的安全性。 若要控制对数据库的访问，一种较为安全的方法是使用 Windows 身份验证（也称为集成安全性）。 有关详细信息，请参阅[保护连接信息](../../data/adonet/protecting-connection-information.md)。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>IDataPageRetriever 接口  
 下面的代码示例定义`IDataPageRetriever`接口，由实现`DataRetriever`类。 在此接口中声明的唯一方法是`SupplyPageOfData`方法，它需要的初始行索引和数据的一页中的行数的计数。 实施者使用这些值来从数据源检索数据的子集。  
  
 一个`Cache`对象使用在构造期间，此接口的实现来加载数据的两个初始页。 无论何时需要未缓存的值，缓存将丢弃这些页之一并请求一个包含中的值的新页面`IDataPageRetriever`。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever 类  
 下面的代码示例定义`DataRetriever`类，该类实现`IDataPageRetriever`接口以从服务器中检索的数据页。 `DataRetriever`类还提供了`Columns`并`RowCount`属性，其中<xref:System.Windows.Forms.DataGridView>控件使用以创建必要的列，并添加适当数量的空的行<xref:System.Windows.Forms.DataGridView.Rows%2A>集合。 添加空的行是必需的因此，控件的行为就好像它包含在表中的所有数据。 这意味着，滚动条中的滚动框将具有适当的大小，并且用户将能够访问表中的任何行。 行填充<xref:System.Windows.Forms.DataGridView.CellValueNeeded>事件处理程序仅当它们滚动到视图时。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>缓存类  
 下面的代码示例定义`Cache`类，该类管理两个通过填充的数据页`IDataPageRetriever`实现。 `Cache`类定义一个内部`DataPage`结构，其中包含<xref:System.Data.DataTable>若要将值存储在单个缓存页，并且计算的行索引表示页的上限和下限边界。  
  
 `Cache`类在构造时加载两个数据页。 每当<xref:System.Windows.Forms.DataGridView.CellValueNeeded>事件请求一个值，`Cache`对象确定值现已推出一个其两个页面，如果是这样，将其返回。 如果值不在本地可用时，`Cache`对象确定这两个页面最当前显示的行和页替换新建一个包含请求的值，然后将其返回。  
  
 假定数据页中的行数是可以同时在屏幕显示的行数相同，此模型允许用户通过表分页若要有效地返回到最近查看的页。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>其他注意事项  
 前面的代码示例演示在实时数据加载提供。 你将需要修改自己的需要来达到最高效率的代码。 最小值，需要在缓存中选择适当的值的数据的每页行数。 此值传递到`Cache`构造函数。 每页行数应为不低于可以同时在显示的行数在<xref:System.Windows.Forms.DataGridView>控件。  
  
 为获得最佳结果，需要进行性能测试和可用性测试，以确定您的系统和用户的要求。 将需要考虑的几个因素包括客户端计算机运行你的应用程序、 可用带宽的使用的网络连接和使用的服务器的滞后时间中的内存量。 带宽和延迟应确定有时的高峰使用期。  
  
 若要提高你的应用程序的滚动性能，可以增加本地存储的数据量。 若要提高启动时间，但是，必须避免最初加载过多的数据。 你可能想要修改`Cache`类，以增加可以存储的数据页的数目。 使用多个数据页可提高滚动效率，但将需要确定的理想数据页中，具体取决于可用带宽和服务器延迟中的行数。 使用较小的页，服务器将更频繁地访问，但需要更少的时间才能返回所请求的数据。 如果延迟的带宽比问题的详细信息，你可能想要使用较大的数据页。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows 窗体 DataGridView 控件中的性能优化](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [缩放 Windows 窗体 DataGridView 控件的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的虚拟模式](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [演练：在 Windows 窗体 DataGridView 控件中实现虚拟模式](implementing-virtual-mode-wf-datagridview-control.md)
- [如何：在 Windows 窗体 DataGridView 控件中实现实时数据加载的虚拟模式](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
