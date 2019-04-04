---
title: 如何：LINQ 查询结果返回为特定的类型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: ba6479852f7a78fb26743a04fd08adea07c1ffff
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835864"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>如何：LINQ 查询结果返回为特定的类型 (Visual Basic)
语言集成查询 (LINQ) 轻松地访问数据库的信息和执行查询。 默认情况下，LINQ 查询以匿名类型返回的对象的列表。 此外可以指定一个查询使用返回特定类型的列表`Select`子句。  
  
 下面的示例演示如何创建新应用程序对 SQL Server 数据库执行查询并将结果投影为特定的命名类型。 有关详细信息，请参阅[匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)并[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。  
  
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
  
2.  单击客户表并将其拖到设计器的左窗格中。  
  
     在设计器创建一个新`Customer`为你的项目的对象。 可以投影查询结果作为`Customer`类型或为您创建的类型。 此示例将在后面的过程中创建新类型和项目与该类型的查询结果。  
  
3.  保存所做的更改并关闭设计器。  
  
4.  保存你的项目。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>添加代码以查询数据库并显示结果  
  
1.  从**工具箱**，拖动<xref:System.Windows.Forms.DataGridView>控件拖到你的项目，Form1 的默认 Windows 窗体上。  
  
2.  双击 Form1 以修改 Form1 类。  
  
3.  之后`End Class`语句的 Form1 类中，添加以下代码以创建`CustomerInfo`类型，以保留此示例的查询结果。  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4.  当表添加到 O/R 设计器时，在设计器添加<xref:System.Data.Linq.DataContext>到你的项目的对象。 此对象包含必须具有访问这些表，以及访问单个对象和集合的每个表的代码。 <xref:System.Data.Linq.DataContext>对象将项目命名为根据.dbml 文件的名称。 对于此项目，<xref:System.Data.Linq.DataContext>对象被命名为`northwindDataContext`。  
  
     可以创建的实例<xref:System.Data.Linq.DataContext>代码和查询中指定由 O/R 设计器的表。  
  
     在`Load`事件 Form1 类中，添加以下代码以查询作为数据上下文的属性公开的表。 `Select`子句的查询将创建一个新`CustomerInfo`类型而不是匿名类型的查询结果的每一项。  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5.  按 F5 以运行您的项目并查看结果。  
  
## <a name="see-also"></a>请参阅

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查询](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext 方法（O/R 设计器）](/visualstudio/data-tools/datacontext-methods-o-r-designer)
