---
title: 迁移注意事项（实体框架）
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: 359e373476398bb26f06eb86eb13296ab05d2705
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089882"
---
# <a name="migration-considerations-entity-framework"></a>迁移注意事项（实体框架）
现有的应用程序可以从多方面受益于 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] 实体框架。 其中最重要的益处之一在于能够使用概念模型将应用程序使用的数据结构与数据源中的架构分离。 这样，日后便可轻松地对存储模型或数据源本身进行更改，而无需对应用程序进行补偿更改。 有关使用的优点的详细信息[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]，请参阅[实体框架概述](../../../../../docs/framework/data/adonet/ef/overview.md)并[实体数据模型](../../../../../docs/framework/data/adonet/entity-data-model.md)。  
  
 为了利用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]的益处，您可以将现有应用程序迁移到[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 某些任务对于所有迁移的应用程序是通用的。 这些通用任务包括升级应用程序以使用[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]从版本 3.5 Service Pack 1 (SP1)、 定义模型和映射以及配置实体框架。 在将应用程序迁移至[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]时，还需要考虑其他一些注意事项。 相关注意事项取决于要迁移的应用程序的类型及具体功能。 本主题提供的信息可帮助您为现有应用程序选择最佳的升级途径。  
  
## <a name="general-migration-considerations"></a>有关迁移的一般注意事项  
 在将任何应用程序迁移到[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]时，需要考虑以下注意事项：  
  
-   使用任何应用程序[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]从版本 3.5 SP1 开始可迁移到实体框架中，只要应用程序使用的数据源的数据提供程序支持实体框架。  
  
-   即使某个数据源提供程序支持实体框架，实体框架也可能不支持该提供程序的所有功能。  
  
-   对于大型或复杂的应用程序，不需要一次性地将整个应用程序迁移到实体框架。 但是，在数据源发生更改时，仍然需要更改应用程序中不使用实体框架的任何部分。  
  
-   应用程序的其他部分可以共享实体框架所用的数据提供程序连接，因为[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]使用 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] 数据提供程序访问数据源。 例如，实体框架使用 SqlClient 提供程序访问 SQL Server 数据库。 有关详细信息，请参阅[针对实体框架的 EntityClient Provider](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)。  
  
## <a name="common-migration-tasks"></a>通用迁移任务  
 将现有应用程序迁移到[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]的途径取决于应用程序的类型以及现有的数据访问策略。 但是，在将现有应用程序迁移到[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]时，总是要执行以下任务。  
  
> [!NOTE]
>  当您使用实体数据模型工具从 Visual Studio 2008 开始，所有这些任务会自动执行。 有关详细信息，请参阅[如何：使用实体数据模型向导](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
1.  升级应用程序。  
  
     通过使用 Visual Studio 的早期版本创建的项目和[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]必须升级为使用 Visual Studio 2008 SP1 和[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]开头版本 3.5 SP1。  
  
2.  定义模型和映射。  
  
     模型和映射文件定义概念模型中的实体、数据源中的结构（如表、存储过程和视图）以及实体与数据源结构之间的映射。 有关详细信息，请参阅[如何：手动定义模型和映射文件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))。  
  
     在存储模型中定义的类型必须与数据源中对象的名称相匹配。 如果现有应用程序将数据作为对象公开，则必须确保在概念模型中定义的实体和属性与这些现有数据类和属性的名称相匹配。 有关详细信息，请参阅[如何：自定义建模和映射文件以使用自定义对象](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100))。  
  
    > [!NOTE]
    >  可以使用实体数据模型设计器重命名概念模型中的实体以匹配现有对象。 有关详细信息，请参阅[实体数据模型设计器](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100))。  
  
3.  定义连接字符串。  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]在对概念模型执行查询时使用特殊格式的连接字符串。 此连接字符串包装有关模型和映射文件和到数据源的连接的信息。 有关详细信息，请参阅[如何：定义连接字符串](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)。  
  
4.  Visual Studio 项目配置。  
  
     对引用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]必须将程序集的模型和映射文件添加到 Visual Studio 项目。 可以将这些映射文件添加到项目中，以确保这些文件随应用程序一起部署在连接字符串中所指示的位置。 有关详细信息，请参阅[如何：手动配置实体框架项目](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))。  
  
## <a name="considerations-for-applications-with-existing-objects"></a>有关包含现有对象的应用程序的注意事项  
 从 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4 开始，[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]就支持“纯旧式”CLR 对象 (POCO)，也称为持久性未知对象。 大多数情况下，通过进行少量修改，现有对象可以使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 有关详细信息，请参阅[使用 POCO 实体](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100))。 此外可以将迁移到应用程序[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]和使用实体框架工具生成的数据类。 有关详细信息，请参阅[如何：使用实体数据模型向导](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>有关使用 ADO.NET 提供程序的应用程序的注意事项  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] 提供程序，例如 SqlClient，使你能够查询要返回表格数据的数据源。 此外可以将数据加载到[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]数据集。 下表介绍在升级使用现有 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] 提供程序的应用程序时的注意事项：  
  
- 使用数据读取器显示表格格式数据。  

  你可能考虑执行[!INCLUDE[esql](../../../../../includes/esql-md.md)]查询使用 EntityClient 提供程序和枚举返回<xref:System.Data.EntityClient.EntityDataReader>对象。 仅当应用程序使用数据读取器显示表格格式数据，且不需要由[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]提供用于将数据具体化为对象、跟踪更改和进行更新的功能时，才应这样做。 可以继续使用对数据源进行更新的现有数据访问代码，但可以使用从 <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> 的 <xref:System.Data.EntityClient.EntityConnection> 属性访问的现有连接。 有关详细信息，请参阅[针对实体框架的 EntityClient Provider](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)。  
  
- 使用数据集。  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]提供了很多相同功能提供的数据集，其中包括内存中持久性、 更改跟踪、 数据绑定以及将对象序列化为 XML 数据。 有关详细信息，请参阅[使用对象](../../../../../docs/framework/data/adonet/ef/working-with-objects.md)。  
  
  如果[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]不提供功能的应用程序所需的数据集，您仍可以充分利用 LINQ 查询的优点使用[!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]。 有关详细信息，请参阅 [LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md)。  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>有关将数据绑定到控件的应用程序的注意事项  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]使您可以如包装在数据源的数据，数据集或[!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]数据源控件，，然后将用户界面元素绑定到这些数据控件。 下表介绍将控件绑定到实体框架数据时的注意事项。  
  
- 将数据绑定到控件。  

  查询概念模型时[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]作为对象的实体类型实例的形式返回的数据。 这些对象可以直接绑定到控件，以及此绑定支持更新。 这意味着，将更改为一个控件，例如中的行中的数据<xref:System.Windows.Forms.DataGridView>，则自动保存到数据库时<xref:System.Data.Objects.ObjectContext.SaveChanges%2A>调用方法。  
  
  如果应用程序对查询结果进行枚举，以在 <xref:System.Windows.Forms.DataGridView> 或支持数据绑定的其他类型的控件中显示数据，则可以修改应用程序以将该控件绑定到 <xref:System.Data.Objects.ObjectQuery%601> 的结果。  
  
  有关详细信息，请参阅[对象绑定到控件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100))。  
  
- [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] 数据源控件。  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]包括用于简化数据绑定中的数据源控件[!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]Web 应用程序。 有关详细信息，请参阅[EntityDataSource Web 服务器控件概述](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100))。  
  
## <a name="other-considerations"></a>其他注意事项  
 以下是在将特定类型的应用程序迁移到实体框架时可能需要考虑的一些注意事项。  
  
- 公开数据服务的应用程序。  

  基于 Windows Communication Foundation (WCF) 的 Web 服务和应用程序使用 XML 请求/响应消息格式公开基础数据源中的数据。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]使用二进制、XML 或 WCF 数据约定序列化支持实体对象的序列化。 二进制和 WCF 序列化都支持对象图的整体序列化。 有关详细信息，请参阅[生成 N 层应用程序](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100))。  
  
- 使用 XML 数据的应用程序。  

  通过对象序列化可以创建[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]数据服务。 这些服务为使用 XML 数据的应用程序（如基于 AJAX 的 Internet 应用程序）提供数据。 在这类情况下，请考虑使用 [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]。 这些数据服务基于实体数据模型和通过使用标准具象状态传输 (REST) HTTP 操作提供对实体数据的动态访问、 如 GET、 PUT 和 POST。 有关详细信息，请参阅 [WCF Data Services 4.5](../../../../../docs/framework/data/wcf/index.md)。  
  
  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]不支持本机 XML 数据类型。 这意味着在将实体映射到包含 XML 列的表时，该 XML 列的等效实体属性是一个字符串。 对象可以断开连接，并序列化为 XML。 有关详细信息，请参阅[序列化对象](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100))。  
  
  如果应用程序需要查询 XML 数据，则仍然可以通过使用 LINQ to XML 来利用 LINQ 查询的优点。 有关详细信息，请参阅[LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)或[LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)。  
  
- 维护状态的应用程序。  

  [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Web 应用程序需要经常维护网页或用户会话的状态。 中的对象<xref:System.Data.Objects.ObjectContext>可以存储在客户端视图状态或在服务器上的会话状态中实例，和更高版本能检索和重新附加到新的对象上下文。 有关详细信息，请参阅[附加和分离对象](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100))。  
  
## <a name="see-also"></a>请参阅

- [部署注意事项](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [实体框架术语](../../../../../docs/framework/data/adonet/ef/terminology.md)
