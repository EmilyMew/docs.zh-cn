---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 44b28ec265a18632e936ba05e25840a03f68da90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119010"
---
# <a name="limit-entity-sql"></a>LIMIT (Entity SQL)
在 ORDER BY 子句中使用 LIMIT 子子句可执行物理分页。 LIMIT 不能脱离 ORDER BY 子句单独使用。  
  
## <a name="syntax"></a>语法  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>自变量  
 `n`  
 将选择的项的数量。  
  
 如果 ORDER BY 子句中存在 LIMIT 表达式子子句，则将根据排序规范对查询排序，并且结果行数将受到 LIMIT 表达式限制。 例如，LIMIT 5 将结果集限制为 5 个实例或行。 LIMIT 的功能与 TOP 相当，区别之处是 LIMIT 要求 ORDER BY 子句存在。 SKIP 和 LIMIT 可独立与 ORDER BY 子句一起使用。  
  
> [!NOTE]
>  如果 TOP 修饰符和 SKIP 子子句出现在同一个查询表达式中，Entity SQL 查询将被视为无效。 应重写查询，将 TOP 表达式更改为 LIMIT 表达式。  
  
## <a name="example"></a>示例  
 下面的 Entity SQL 查询将 LIMIT 和 ORDER BY 运算符结合使用来指定用于 SELECT 语句所返回的对象的排序顺序。 此查询基于 AdventureWorks 销售模型。 若要编译并运行此查询，请执行下列步骤：  
  
1.  按照中的过程[如何：执行返回 StructuralType 结果的查询](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。  
  
2.  将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>请参阅

- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [如何：页查看查询结果](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [分页](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
