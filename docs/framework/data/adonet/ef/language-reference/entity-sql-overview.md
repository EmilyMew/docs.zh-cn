---
title: Entity SQL 概述
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 100d616462cd76e1dde8fc855787ec3118842fc8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073465"
---
# <a name="entity-sql-overview"></a>Entity SQL 概述
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 是一种类似 SQL 的语言，可用于查询中的概念模型[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]。 概念模型表示为实体和关系数据和[!INCLUDE[esql](../../../../../../includes/esql-md.md)]可以查询这些实体和关系所熟悉的用户使用过 SQL 的格式。  
  
 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 使用存储特定的数据提供程序，将一般 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 转换为存储特定的查询。 EntityClient 提供程序提供一种方式，用于针对实体模型执行 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 命令并返回包括标量结果、结果集和对象图在内的丰富类型数据。 构造 <xref:System.Data.EntityClient.EntityCommand> 对象时，可以指定一个存储过程名称或者通过将 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询字符串分配该对象的 <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> 属性来指定查询文本。 <xref:System.Data.EntityClient.EntityDataReader> 公开对 EDM 执行 <xref:System.Data.EntityClient.EntityCommand> 的结果。 若要执行返回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，请调用 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。  
  
 除了 EntityClient 提供程序之外，[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]还允许您使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 对概念模型执行查询，并以强类型 CLR 对象的形式返回数据，这些对象是实体类型的实例。 有关详细信息，请参阅[使用对象](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md)。  
  
 本节提供 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 的概念信息。  
  
## <a name="in-this-section"></a>本节内容  
 [Entity SQL 与 Transact-SQL 有何不同](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [Entity SQL 快速参考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [类型系统](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [类型定义](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [构造类型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [查询计划缓存](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [命名空间](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [标识符](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [参数](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [变量](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [不支持的表达式](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [文本](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [NULL 文本和类型推理](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [输入字符集](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [查询表达式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [函数](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [运算符优先级](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [分页](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [比较语义](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [撰写嵌套的 Entity SQL 查询](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [可以为 NULL 的结构化类型](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>请参阅

- [实体 SQL 引用](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL 语言](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [CSDL、SSDL 和 MSL 规范](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
