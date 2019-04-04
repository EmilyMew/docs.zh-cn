---
title: 如何：使用 LINQ (Visual Basic 中) 调用存储的过程
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 2d05d43ae8f9b93fd3e5e405bb7ff0d59832e830
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823345"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>如何：使用 LINQ (Visual Basic 中) 调用存储的过程
语言集成查询 (LINQ)，使得可以轻松地访问数据库的信息，包括数据库对象，如存储过程。  
  
 下面的示例演示如何创建 SQL Server 数据库中调用存储的过程的应用程序。 此示例演示如何调用数据库中的两个不同的存储的过程。 每个过程返回查询的结果。 一个过程将输入的参数，而其他过程不使用参数。  
  
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
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>若要将存储的过程添加到 O/R 设计器  
  
1.  在中**服务器资源管理器**/**数据库资源管理器**，扩展连接到 Northwind 数据库。 展开**存储过程**文件夹。  
  
     如果已关闭 O/R 设计器，您可以通过双击前面添加的 northwind.dbml 文件重新打开它。  
  
2.  单击**基于年份的销售额**存储过程并将其拖到设计器的右窗格中。 单击**Ten Most Expensive Products**存储的过程将将其拖到设计器的右窗格中。  
  
3.  保存所做的更改并关闭设计器。  
  
4.  保存你的项目。  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>若要添加代码以显示存储过程的结果  
  
1.  从**工具箱**，拖动<xref:System.Windows.Forms.DataGridView>控件拖到你的项目，Form1 的默认 Windows 窗体上。  
  
2.  双击 Form1 以将代码添加到其`Load`事件。  
  
3.  当存储的过程添加到 O/R 设计器中时，在设计器添加<xref:System.Data.Linq.DataContext>为你的项目的对象。 此对象包含必须具有访问这些过程的代码。 <xref:System.Data.Linq.DataContext>对象项目命名为根据.dbml 文件的名称。 对于此项目，<xref:System.Data.Linq.DataContext>对象被命名为`northwindDataContext`。  
  
     可以创建的实例<xref:System.Data.Linq.DataContext>O/R 设计器中，代码并调用指定的存储的过程方法。 若要将绑定到<xref:System.Windows.Forms.DataGridView>对象，你可能必须强制查询立即执行通过调用<xref:System.Linq.Enumerable.ToList%2A>方法上的存储过程的结果。  
  
     将以下代码添加到`Load`事件以调用存储过程公开为数据上下文的方法之一。  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4.  按 F5 以运行您的项目并查看结果。  
  
## <a name="see-also"></a>请参阅

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查询](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext 方法（O/R 设计器）](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [如何：分配存储过程以便执行更新、插入和删除操作（O/R 设计器）](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
