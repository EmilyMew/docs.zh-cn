---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 57f7c61d8e4de2a63708ef6d4437ca53de854af9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116857"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)
取消引用一个引用值，并生成该取消引用的结果。  
  
## <a name="syntax"></a>语法  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a>自变量  
 `expression`  
 任何返回集合的有效查询表达式。  
  
## <a name="return-value"></a>返回值  
 引用的实体的值。  
  
## <a name="remarks"></a>备注  
 DEREF 运算符取消引用一个引用值，并生成该取消引用的结果。 例如，如果`r`为 ref 类型引用\<T >，`Deref(r)`类型的表达式`T`生成的引用的实体`r`。 如果引用值为 Null，或无关联（即，引用的目标不存在），则 DEREF 运算符的结果为 Null。  
  
## <a name="example"></a>示例  
 下面的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询使用 DEREF 运算符取消引用一个引用值，并生成该取消引用的结果。 此查询基于 AdventureWorks 销售模型。 若要编译并运行此查询，请执行下列步骤：  
  
1.  按照中的过程[如何：执行返回 PrimitiveType 结果的查询](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。  
  
2.  将以下查询作为参数传递给 ExecutePrimitiveTypeQuery 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a>请参阅

- [实体 SQL 引用](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [可以为 NULL 的结构化类型](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
