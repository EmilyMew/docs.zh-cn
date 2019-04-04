---
title: 如何：通过使用 LINQ (Visual Basic 中) 来修改数据库中的数据
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: c92a94cd6223aad8e4ea3da86a8dd37bd71aad2c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820992"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>如何：通过使用 LINQ (Visual Basic 中) 来修改数据库中的数据
语言集成查询 (LINQ) 查询轻松访问数据库的信息和修改数据库中的值。  
  
 下面的示例演示如何创建新的应用程序检索和更新信息的 SQL Server 数据库中。  
  
 本主题中的示例使用 Northwind 示例数据库。 如果在开发计算机上没有此数据库，您可以从 Microsoft 下载中心下载它。 有关说明，请参阅[下载示例数据库](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
### <a name="to-create-a-connection-to-a-database"></a>若要创建与数据库的连接  
  
1.  在 Visual Studio 中打开**服务器资源管理器**/**数据库资源管理器**通过单击**视图**菜单，并选择**服务器资源管理器**/**数据库资源管理器**。  
  
2.  右键单击**数据连接**中**服务器资源管理器**/**数据库资源管理器**，然后单击**添加连接**。  
  
3.  指定到 Northwind 示例数据库的有效连接。  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>若要将使用 LINQ 项目添加到 SQL 文件  
  
1.  在 Visual Studio 中的“文件”菜单上，指向“新建”，然后单击“项目”。 选择 Visual Basic **Windows 窗体应用程序**作为项目类型。  
  
2.  在 **“项目”** 菜单上，单击 **“添加新项”**。 选择**LINQ to SQL 类**项模板。  
  
3.  为 `northwind.dbml` 文件命名。 单击 **添加**。 对象关系设计器 （O/R 设计器） 打开供`northwind.dbml`文件。  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>若要添加表查询和修改到设计器  
  
1.  在中**服务器资源管理器**/**数据库资源管理器**，扩展连接到 Northwind 数据库。 展开**表**文件夹。  
  
     如果已关闭 O/R 设计器，你可以重新打开它通过双击`northwind.dbml`前面添加的文件。  
  
2.  单击客户表并将其拖到设计器的左窗格中。  
  
     在设计器创建新的 Customer 对象为你的项目。  
  
3.  保存所做的更改并关闭设计器。  
  
4.  保存你的项目。  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>添加代码以修改数据库并显示结果  
  
1.  从**工具箱**，拖动<xref:System.Windows.Forms.DataGridView>控件拖到你的项目，Form1 的默认 Windows 窗体上。  
  
2.  当表添加到 O/R 设计器时，在设计器添加<xref:System.Data.Linq.DataContext>到你的项目的对象。 此对象包含可用于访问客户表的代码。 它还包含用于定义本地客户对象和表的客户集合的代码。 <xref:System.Data.Linq.DataContext>对象将项目命名为根据.dbml 文件的名称。 对于此项目，<xref:System.Data.Linq.DataContext>对象被命名为`northwindDataContext`。  
  
     可以创建的实例<xref:System.Data.Linq.DataContext>中您的代码和查询对象并修改指定由 O/R 设计器的客户集合。 之前通过调用将其提交到的客户集合所做的更改不会反映在数据库中<xref:System.Data.Linq.DataContext.SubmitChanges%2A>方法的<xref:System.Data.Linq.DataContext>对象。  
  
     双击 Windows 窗体，Form1，若要将代码添加到<xref:System.Windows.Forms.Form.Load>作为属性公开的 Customers 表的查询的事件在<xref:System.Data.Linq.DataContext>。 添加以下代码：  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  从**工具箱**，将三个<xref:System.Windows.Forms.Button>拖到窗体控件。 选择第一个`Button`控件。 在中**属性**窗口中，将`Name`的`Button`控制对`AddButton`并`Text`到`Add`。 选择第二个按钮，然后设置`Name`属性设置为`UpdateButton`并`Text`属性设置为`Update`。 选择第三个按钮，然后设置`Name`属性设置为`DeleteButton`并`Text`属性设置为`Delete`。  
  
4.  双击**外**按钮以将代码添加到其`Click`事件。 添加以下代码：  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  双击**更新**按钮以将代码添加到其`Click`事件。 添加以下代码：  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  双击**删除**按钮以将代码添加到其`Click`事件。 添加以下代码：  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  按 F5 运行项目。 单击**添加**添加新记录。 单击**更新**修改新记录。 单击**删除**删除新记录。  
  
## <a name="see-also"></a>请参阅

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查询](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext 方法（O/R 设计器）](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [如何：分配存储过程以便执行更新、插入和删除操作（O/R 设计器）](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
