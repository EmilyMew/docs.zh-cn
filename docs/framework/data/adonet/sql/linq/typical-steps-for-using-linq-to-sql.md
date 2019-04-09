---
title: 使用 LINQ to SQL 的典型步骤
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: a7c6257bc27728d101d64d07ffedb1e38bc994eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132842"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>使用 LINQ to SQL 的典型步骤
若要实现 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 应用程序，请按照本主题后面部分说明的步骤操作。 请注意，很多步骤是可选的。 您可以以对象模型的默认状态使用它，这种可能性很高。  
  
 为了很快入手，请使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 来创建对象模型并开始编写查询代码。  
  
## <a name="creating-the-object-model"></a>创建对象模型  
 第一步是用现有关系数据库的元数据创建对象模型。 对象模型按照开发人员所用的编程语言来表示数据库。 有关详细信息，请参阅[LINQ to SQL 对象模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)。  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1.选择用于创建模型的工具。  
 有三种工具可用于创建模型。  
  
-   必须向 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]  
  
     此设计器提供了用于从现有数据库创建对象模型的丰富用户界面。 此工具是 Visual Studio IDE 的一部分，最适合于小型或中型数据库。  
  
-   SQLMetal 代码生成工具  
  
     此命令行实用工具提供了与 [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]略微不同的一组选项。 最好使用此工具对大型数据库进行建模。 有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。  
  
-   代码编辑器  
  
     可以通过使用 Visual Studio 代码编辑器或其他编辑器编写你自己的代码。 我们建议，在您具有现有数据库且可以使用 [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]或 SQLMetal 工具时不要使用这种方法，因为这种方法容易出错。 但是，代码编辑器在改进或修改你已通过使用其他工具生成的代码方面非常有用。 有关详细信息，请参阅[如何：通过使用代码编辑器自定义实体类](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)。  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2.选择你要生成的代码类型。  
  
-   一个C#或 Visual Basic 源代码文件进行基于属性的映射。  
  
     然后，在 Visual Studio 项目中将此代码文件。 有关详细信息，请参阅[基于属性的映射](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)。  
  
-   用于外部映射的 XML 文件。  
  
     通过使用此方法，你可以将映射元数据放在应用程序代码外部。 有关详细信息，请参阅[外部映射](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]不支持生成外部映射文件。 您必须使用 SQLMetal 工具来实现此功能。  
  
-   DBML 文件，你可以在生成最终代码文件之前修改此文件。  
  
     这是一项高级功能。  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3.改进代码文件以反映你的应用程序的需要。  
 为此，你可以使用 [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]或代码编辑器。  
  
## <a name="using-the-object-model"></a>使用对象模型  
 下图显示了在两层方案中开发人员与数据之间的关系。 有关其他方案，请参阅[N 层和远程应用程序使用 LINQ 到 SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)。  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 既然您已经有了对象模型，您就可以在该模型中描述信息请求和操作数据。 您应从对象模型中的对象和属性的角度来考虑，而不是从数据库的行和列的角度来考虑。 您不是直接对数据库进行操作。  
  
 当您指示 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 执行您已描述的查询或对您已操作的数据调用 `SubmitChanges()` 时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会用数据库的语言与数据库通信。  
  
 以下内容代表使用您已创建的对象模型的典型步骤。  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1.创建查询以从数据库中检索信息。  
 有关详细信息，请参阅[查询概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)并[查询示例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)。  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2.重写 Insert、Update 和 Delete 的默认行为。  
 这一步是可选的。 有关详细信息，请参阅[自定义插入、 更新和删除操作](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3.设置适当的选项以检测和报告并发冲突。  
 您可以保留模型用于处理并发冲突的默认值，也可以根据您的需要对其进行更改。 有关详细信息，请参阅[如何：指定针对并发冲突对哪些成员进行测试](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)和[如何：指定引发时并发异常](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)。  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4.建立继承层次结构。  
 这一步是可选的。 有关详细信息，请参阅[层次结构支持](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)。  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5.提供合适的用户界面。  
 这一步是可选的，取决于您的应用程序的使用方式。  
  
### <a name="6-debug-and-test-your-application"></a>6.调试并测试应用程序。  
 有关详细信息，请参阅[调试支持](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)。  
  
## <a name="see-also"></a>请参阅

- [入门](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
- [创建对象模型](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [存储过程](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
