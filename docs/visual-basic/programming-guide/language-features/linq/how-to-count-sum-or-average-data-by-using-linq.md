---
title: 如何：计数、 求和或通过使用 LINQ (Visual Basic 中) 的平均数据
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: 3ee518928bccaedeaa54c642944ff4e73620ef39
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819131"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a>如何：计数、 求和或通过使用 LINQ (Visual Basic 中) 的平均数据
语言集成查询 (LINQ) 轻松地访问数据库的信息和执行查询。  
  
 下面的示例演示如何创建新的应用程序对 SQL Server 数据库执行查询。 示例计数、 求和，和使用计算结果的平均值`Aggregate`和`Group By`子句。 有关详细信息，请参阅[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)并[组 By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
 本主题中的示例使用 Northwind 示例数据库。 如果在开发计算机上没有此数据库，您可以从 Microsoft 下载中心下载它。 有关说明，请参阅[下载示例数据库](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>若要创建与数据库的连接  
  
1.  在 Visual Studio 中打开**服务器资源管理器**/**数据库资源管理器**通过单击**服务器资源管理器**/**数据库资源管理器**上**视图**菜单。  
  
2.  右键单击**数据连接**中**服务器资源管理器**/**数据库资源管理器**，然后单击**添加连接**。  
  
3.  指定到 Northwind 示例数据库的有效连接。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>若要添加包含 LINQ to SQL 文件的项目  
  
1.  在 Visual Studio 中的“文件”菜单上，指向“新建”，然后单击“项目”。 选择 Visual Basic **Windows 窗体应用程序**作为项目类型。  
  
2.  在 **“项目”** 菜单上，单击 **“添加新项”**。 选择**LINQ to SQL 类**项模板。  
  
3.  为 `northwind.dbml` 文件命名。 单击 **添加**。 此时，northwind.dbml 文件打开时对象关系设计器 （O/R 设计器）。  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>若要添加到 O/R 设计器查询的表  
  
1.  在中**服务器资源管理器**/**数据库资源管理器**，扩展连接到 Northwind 数据库。 展开**表**文件夹。  
  
     如果已关闭 O/R 设计器，您可以通过双击前面添加的 northwind.dbml 文件重新打开它。  
  
2.  单击客户表并将其拖到设计器的左窗格中。 单击订单表并将其拖到设计器的左窗格中。  
  
     在设计器创建新`Customer`和`Order`为你的项目的对象。 请注意，在设计器会自动检测表之间的关系并创建子相关对象的属性。 例如，IntelliSense 将显示`Customer`对象具有`Orders`与该客户相关的所有订单的属性。  
  
3.  保存所做的更改并关闭设计器。  
  
4.  保存你的项目。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>添加代码以查询数据库并显示结果  
  
1.  从**工具箱**，拖动<xref:System.Windows.Forms.DataGridView>控件拖到你的项目，Form1 的默认 Windows 窗体上。  
  
2.  双击 Form1 以将代码添加到`Load`窗体的事件。  
  
3.  当表添加到 O/R 设计器时，在设计器添加<xref:System.Data.Linq.DataContext>为你的项目的对象。 此对象包含必须具有访问这些表，以及访问单个对象和集合的每个表的代码。 <xref:System.Data.Linq.DataContext>对象将项目命名为根据.dbml 文件的名称。 对于此项目，<xref:System.Data.Linq.DataContext>对象被命名为`northwindDataContext`。  
  
     可以创建的实例<xref:System.Data.Linq.DataContext>代码和查询中指定由 O/R 设计器的表。  
  
     将以下代码添加到`Load`事件来查询公开为属性的表在<xref:System.Data.Linq.DataContext>计数、 求和，并计算平均值。 此示例使用`Aggregate`到单个结果的查询子句和`Group By`子句以显示为平均值分组结果。  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4.  按 F5 以运行您的项目并查看结果。  
  
## <a name="see-also"></a>请参阅

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查询](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext 方法（O/R 设计器）](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Group By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)
