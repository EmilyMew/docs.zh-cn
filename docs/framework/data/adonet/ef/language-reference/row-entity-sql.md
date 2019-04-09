---
title: ROW (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 9515d972addc3dd10a27ffbe7776f77d097a30d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074256"
---
# <a name="row-entity-sql"></a>ROW (Entity SQL)
从一个或多个值构造结构上类型化的匿名记录。  
  
## <a name="syntax"></a>语法  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>自变量  
 `expression`  
 任何有效的查询表达式，该表达式返回要在行类型中构造的值。  
  
 `alias`  
 为在行类型中指定的值指定别名。 如果未提供别名，则 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 会尝试基于 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 别名生成规则来生成别名。  
  
## <a name="return-value"></a>返回值  
 一个行类型。  
  
## <a name="remarks"></a>备注  
 使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的行构造函数可以从一个或多个值构造结构上类型化的匿名记录。 行构造函数的结果类型为行类型，其字段类型对应于用于构造该行的值的类型。 例如，下面的表达式构造一个类型为 `Record(a int, b string, c int)`的值。  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 如果没有为行构造函数中的表达式提供别名，则实体框架会尝试生成一个别名。 有关更多信息，请参见 [标识符](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) 主题中的“别名规则”一节。  
  
 以下规则适用于在行构造函数中指定表达式别名：  
  
-   行构造函数中的表达式不能引用同一构造函数中的其他别名。  
  
-   同一行构造函数中的两个表达式不能具有相同别名。  
  
 有关查询构造函数的详细信息，请参阅[构造类型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)。  
  
## <a name="example"></a>示例  
 下面的 Entity SQL 查询使用 ROW 运算符构造结构上类型化的匿名记录。 此查询基于 AdventureWorks 销售模型。 若要编译并运行此查询，请执行下列步骤：  
  
1.  按照中的过程[如何：执行返回 StructuralType 结果的查询](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。  
  
2.  将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>请参阅

- [构造类型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [实体 SQL 引用](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [类型定义](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
