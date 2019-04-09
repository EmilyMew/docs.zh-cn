---
title: 开始使用 Azure 表存储使用F#
description: 使用 Azure 表存储或 Azure Cosmos DB 在云中存储结构化的数据。
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 54c777acd454e4f675175b814675c185e41ad9a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086697"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>开始使用 Azure 表存储和使用 F 在 Azure Cosmos DB 表 API\#

Azure 表存储是一种服务，将结构化的 NoSQL 数据存储在云中。 表存储是采用无架构设计的键/属性存储。 表存储是无架构，因为它很容易使数据适应需求的应用程序发展。 对数据的访问是快速且经济高效的所有类型的应用程序。 表存储是通常显著较低的成本比传统 SQL 要类似的数据卷。

可以使用表存储来存储灵活的数据集，例如 web 应用程序、 地址簿、 设备信息和任何其他类型的服务所需的元数据的用户数据。 可以在表中存储任意数量的实体和存储帐户可以包含任意数量的表，直至达到存储帐户的容量极限。

Azure Cosmos DB 提供的表 API 的应用程序，针对 Azure 表存储编写的这需要进行高级功能，如：

- 统包全局分发。
- 全球范围内的专用的吞吐量。
- 在第 99 个百分点值的个位数的毫秒级延迟。
- 保证高可用性。
- 自动辅助索引。

为 Azure 表存储编写的应用程序可以不更改代码中使用表 API 迁移到 Azure Cosmos DB，并充分利用高级功能。 表 API 有.NET、 Java、 Python 和 Node.js 客户端 Sdk 可用。

有关详细信息，请参阅[Azure Cosmos DB 表 API 简介](https://docs.microsoft.com/azure/cosmos-db/table-introduction)。

## <a name="about-this-tutorial"></a>有关本教程

本教程演示如何编写F#代码来执行某些常见任务，使用 Azure 表存储或 Azure Cosmos DB 表 API，包括创建和删除表和插入、 更新、 删除和查询表数据。

## <a name="prerequisites"></a>系统必备

若要使用本指南，您必须首先[创建 Azure 存储帐户](/azure/storage/storage-create-storage-account)或[Azure Cosmos DB 帐户](https://azure.microsoft.com/try/cosmosdb/)。

## <a name="create-an-f-script-and-start-f-interactive"></a>创建F#脚本并启动F#交互式

这篇文章中的示例可在F#应用程序或F#脚本。 若要创建F#脚本，创建的文件`.fsx`扩展，例如`tables.fsx`，在你F#开发环境。

接下来，使用[程序包管理器](package-management.md)如[paket 依存](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)安装`WindowsAzure.Storage`程序包和引用`WindowsAzure.Storage.dll`使用在脚本中`#r`指令。 再次执行此操作`Microsoft.WindowsAzure.ConfigurationManager`以获取 Microsoft.Azure 命名空间。

### <a name="add-namespace-declarations"></a>添加命名空间声明

添加以下`open`顶部的语句`tables.fsx`文件：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>获取 Azure 存储连接字符串

如果要连接到 Azure 存储表服务，将在本教程中需要你的连接字符串。 您可以从 Azure 门户复制连接字符串。 有关连接字符串的详细信息，请参阅[配置存储连接字符串](/azure/storage/storage-configure-connection-string)。

### <a name="get-your-azure-cosmos-db-connection-string"></a>获取 Azure Cosmos DB 连接字符串

如果要连接到 Azure Cosmos DB，将在本教程中需要你的连接字符串。 您可以从 Azure 门户复制连接字符串。 在 Azure 门户中，在 Cosmos DB 帐户中，转到**设置** > **连接字符串**，然后单击**复制**按钮复制主连接字符串。 

本教程中，在脚本中，如下例所示输入你的连接字符串：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

但是，这是**不建议这样做**为实际项目。 你的存储帐户密钥是类似于你的存储帐户的根密码。 始终要小心保护存储帐户密钥。 避免将其分发给其他用户，硬编码，或将其保存在其他人可以访问的纯文本格式的文件。 您可以重新生成你使用 Azure 门户，如果你认为可能已泄露的密钥。

为实际的应用程序，维护存储连接字符串的最佳方法是在配置文件中。 若要从配置文件中提取的连接字符串，可以执行此操作：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

使用 Azure 配置管理器是可选的。 此外可以使用诸如.NET Framework 的 API`ConfigurationManager`类型。

### <a name="parse-the-connection-string"></a>分析连接字符串

若要分析的连接字符串，请使用：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

这将返回`CloudStorageAccount`。

### <a name="create-the-table-service-client"></a>创建表服务客户端

`CloudTableClient`类可用于检索表和表存储中的实体。 下面是创建服务客户端的一种方法：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

现在已准备好编写代码，读取数据并将数据写入表存储。

### <a name="create-a-table"></a>创建表

此示例演示如何创建一个表，如果尚不存在：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>向表中添加实体

实体具有继承的类型为`TableEntity`。 您可以扩展`TableEntity`在任何方式进行，但您的类型*必须*具有无参数构造函数。 同时具有的属性`get`和`set`存储在 Azure 表中。

实体的分区键和行键唯一地标识表中的实体。 可以快于不同的分区键的查询具有相同的分区键的实体，但使用不同的分区键可实现更高的并行操作的可伸缩性。

下面是举例`Customer`，它使用`lastName`作为分区键和`firstName`作为行键。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

现在，添加`Customer`到表。 若要执行此操作，创建`TableOperation`的表执行。 在这种情况下，创建`Insert`操作。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>插入一批实体

可以将一批实体插入表使用一次写入操作。 批处理操作，可将操作合并成单个执行，但它们有一些限制：

- 您可以执行更新、 删除和插入相同的批处理操作中。
- 批处理操作可包含最多 100 个实体。
- 批处理操作中的所有实体都必须都具有相同的分区键。
- 虽然可能要执行批处理操作中的查询，但它必须是批处理中仅有的操作。

下面是一些代码，将两个插入合并到批处理操作：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>检索分区中的所有实体

若要查询表以获取分区中的所有实体，请使用`TableQuery`对象。 在这里，您筛选实体"Smith"分区键为。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

现在打印结果：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>检索分区中的实体的一部分

如果不想查询分区中的所有实体，则可以通过结合使用分区键筛选器与行键筛选器指定范围。 在这里，你使用两个筛选器来获取"Smith"分区的所有实体的行键 （名字） 以字母开头早于字母表中的"M"。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

现在打印结果：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>检索单个实体

可以编写一个查询来检索单个特定实体。 在这里，使用`TableOperation`来指定客户"Ben Smith"。 而不是一个集合，您会得到`Customer`。 在查询中指定分区键和行键是从表服务中检索单个实体的最快方法。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

现在打印结果：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>替换实体

若要更新实体，从表服务中检索它，修改实体对象，然后将所做的更改保存回表服务使用`Replace`操作。 这会导致在服务器上完全替换该实体，除非在服务器上的该实体自检索之后，则操作将失败这种情况下发生更改。 此失败将防止无意中覆盖来自其他源的更改应用程序。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>插入或替换实体

有时，你不知道实体是否存在于表中。 如果是这样，不再需要在其中存储的当前值。 可以使用`InsertOrReplace`创建实体，或如果它存在，而不考虑其状态，则替换它。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>查询一部分实体属性

表查询可以检索的几个属性，而不是所有这些实体中。 此方法称为投影，可以提高查询性能，尤其适用于大型实体。 在这里，返回使用只需电子邮件地址`DynamicTableEntity`和`EntityResolver`。 请注意，不支持投影在本地存储仿真程序，因此此代码只在表服务使用的帐户时才能运行。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>以异步方式检索页中的实体

如果你正在阅读大量实体，并且你想要检索它们，而不是等待其全部返回，您可以使用分段的查询时进行处理。 在这里，您返回结果在页中使用的异步工作流，以便在等待对于大型要返回的结果集时，不会阻止执行。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

您现在以同步方式执行此计算：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>删除实体

在检索后，可以删除实体。 使用更新实体，此操作失败如果该实体自从您检索到它以后发生更改。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>删除表

您可以从存储帐户中删除表。 已删除的表将不可用的一小段时间之后必须重新创建。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>后续步骤

现在，你已了解表存储的基础知识，单击下面的链接可了解更复杂的存储任务和 Azure Cosmos DB 表 API。

- [Azure Cosmos DB 表 API 简介](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [存储客户端库.NET 参考](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Azure 存储类型提供程序](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Azure 存储团队博客](https://blogs.msdn.com/b/windowsazurestorage/)
- [配置连接字符串](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [在.NET 中的 Azure 表存储入门](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
