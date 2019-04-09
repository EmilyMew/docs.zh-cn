---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: bbc3ffd4902fe8c1c41aebe88317d0e3c32f7771
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077090"
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)
从查询表达式返回特定类型的对象集合。  
  
## <a name="syntax"></a>语法  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>自变量  
 `expression`  
 返回对象集合的任何有效的查询表达式。  
  
 `test_type`  
 要对 `expression` 返回的每个对象进行测试的类型。 该类型必须由命名空间进行限定。  
  
## <a name="return-value"></a>返回值  
 `test_type`类型或 `test_type`的基类型或派生类型的对象集合。 如果指定 ONLY，则仅返回 `test_type` 的实例或空集合。  
  
## <a name="remarks"></a>备注  
 `OFTYPE` 表达式指定一个类型表达式，此表达式旨在针对集合的每个元素执行类型测试。  `OFTYPE` 表达式生成指定类型的新集合，其中仅包含等效于该类型或其子类型的元素。  
  
 `OFTYPE` 表达式是下面的查询表达式的缩写形式：  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 如果 Manager 是 Employee 的子类型，则以下表达式将从员工集合生成仅包含经理的集合：  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 还可以使用类型筛选器向上转换集合类型：  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 因为所有执行官都是经理，所以结果集合仍然包含原来的所有执行官，但该集合现在的类型却是经理的集合。  
  
 下表显示了 `OFTYPE` 运算符对于某些模式的行为。 所有异常都在调用提供程序之前从客户端引发：  
  
|模式|行为|  
|-------------|--------------|  
|OFTYPE(Collection(EntityType), EntityType)|Collection(EntityType)|  
|OFTYPE(Collection(ComplexType), ComplexType)|引发|  
|OFTYPE(Collection(RowType), RowType)|引发|  
  
## <a name="example"></a>示例  
 下面的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询使用 OFTYPE 运算符从 Course 对象集合返回 OnsiteCourse 对象集合。 该查询基于 [School 模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))。  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a>请参阅

- [实体 SQL 引用](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
