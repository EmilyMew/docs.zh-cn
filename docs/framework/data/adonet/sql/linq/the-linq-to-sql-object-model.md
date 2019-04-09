---
title: LINQ to SQL 对象模型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: 7ce759de004d479f5162d2ce3a965f5c40afa450
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110788"
---
# <a name="the-linq-to-sql-object-model"></a>LINQ to SQL 对象模型
在[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，开发人员的编程语言表示的对象模型映射到关系数据库的数据模型。 然后就会按照对象模型来执行对数据的操作。  
  
 在这种情况下，您无需向数据库发出数据库命令（例如，`INSERT`）， 而是在对象模型中更改值和执行方法。 当您需要查询数据库或向其发送更改时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会将您的请求转换成正确的 SQL 命令，然后将这些命令发送到数据库。  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 下表概括了 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 对象模型中最基本的元素及其与关系数据模型中的元素的关系：  
  
|LINQ to SQL 对象模型|关系数据模型|  
|------------------------------|---------------------------|  
|实体类|表|  
|类成员|列|  
|关联|外键关系|  
|方法|存储过程或函数|  
  
> [!NOTE]
>  以下说明假定您已具备关系数据模型和规则方面的基础知识。  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>LINQ to SQL 实体类与数据库表  
 在中[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，由表示数据库表*实体类*。 实体类与您可能创建的任何其他类相似，只不过对实体类进行批注的方法是使用将该类与数据库表关联的特殊信息。 您需通过向类声明中添加自定义属性 (<xref:System.Data.Linq.Mapping.TableAttribute>) 来进行这种批注，如下面的示例所示：  
  
### <a name="example"></a>示例  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 只有声明为表的类（即实体类）的实例才能保存到数据库中。  
  
 有关详细信息，请参阅的表属性部分[基于属性的映射](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)。  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>LINQ to SQL 类成员与数据库列  
 除了将类与表关联以外，您还需指定字段或属性来表示数据库列。 为此，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 定义了 <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性，如下面的示例所示：  
  
### <a name="example"></a>示例  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 只有映射到列的字段和属性才能持久保存到数据库中，从数据库中也只能检索这样的字段和属性。 那些未声明为列的字段和属性被视为应用程序逻辑的瞬态部分。  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性 (Attribute) 具有各种属性 (Property)，您可以使用这些属性 (Property) 来自定义表示列的这些成员（例如，将某一成员指定为表示主键列）。 有关详细信息，请参阅的列属性部分[基于属性的映射](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)。  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>LINQ to SQL 关联与数据库外键关系  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，数据库关联（如外键到主键关系）是通过应用 <xref:System.Data.Linq.Mapping.AssociationAttribute> 属性表示的。 在下面的代码段中，`Order` 类包含具有 `Customer` 属性 (Attribute) 的 <xref:System.Data.Linq.Mapping.AssociationAttribute> 属性 (Property)。 此属性 (Property) 及其属性 (Attribute) 为 `Order` 类提供了与 `Customer` 类的关系。  
  
 下面的代码示例显示了 `Customer` 类中的 `Order` 属性 (Property)。  
  
### <a name="example"></a>示例  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 有关详细信息，请参阅的关联属性部分[基于属性的映射](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)。  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>LINQ to SQL 方法与数据库存储过程  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支持存储过程和用户定义的函数。 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，您应将数据库定义的这些抽象映射到客户端对象，以便您可以从客户端代码中以强类型化方式访问它们。 方法签名与数据库中定义的过程和函数的签名尽可能类似。 您可以使用 IntelliSense 来查找这些方法。  
  
 通过调用映射的过程返回的结果集为强类型化的集合。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 存储的过程和函数映射到方法通过使用<xref:System.Data.Linq.Mapping.FunctionAttribute>和<xref:System.Data.Linq.Mapping.ParameterAttribute>属性。 表示存储过程的方法与表示用户定义的函数的方法通过 <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> 属性加以区分。 如果此属性设置为 `false`（默认值），则此方法表示存储过程。 如果它设置为 `true`，则此方法表示数据库函数。  
  
> [!NOTE]
>  如果使用的 Visual Studio，则可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]创建映射到存储的过程和用户定义函数的方法。  
  
### <a name="example"></a>示例  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 有关详细信息，请参阅的函数属性，存储过程属性和参数属性部分[基于属性的映射](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)并[存储过程](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)。  
  
## <a name="see-also"></a>请参阅

- [基于特性的映射](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [背景信息](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
