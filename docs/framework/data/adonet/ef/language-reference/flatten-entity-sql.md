---
title: FLATTEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 76fba91f27479df19bbc4ac6e120d615a16f1d42
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115110"
---
# <a name="flatten-entity-sql"></a>FLATTEN (Entity SQL)
将一个由多个集合组成的集合转换为一个平展集合。 新集合与旧集合包含所有相同的元素，但没有嵌套结构。  
  
## <a name="syntax"></a>语法  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>自变量  
 `collection`  
 任何有效的表达式，该表达式返回一个由值集合组成的集合以平展为单个集合。  
  
## <a name="remarks"></a>备注  
 `FLATTEN` 是的一个[!INCLUDE[esql](../../../../../../includes/esql-md.md)]集运算符。 所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符都是从左到右进行求值。 请参阅[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)有关优先级信息[!INCLUDE[esql](../../../../../../includes/esql-md.md)]集运算符。  
  
## <a name="example"></a>示例  
 以下 Entity SQL 查询使用 `FLATTEN` 运算符以将一个由多个集合组成的集合转换为一个平展集合。 若要编译并运行此查询，请执行下列步骤：  
  
1.  按照中的过程[如何：执行返回 StructuralType 结果的查询](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。  
  
2.  将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a>请参阅

- [实体 SQL 引用](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
