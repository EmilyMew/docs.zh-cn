---
title: 聚合函数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: 113c19078feeca24a0817e52f8eb0d04537b0684
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104918"
---
# <a name="aggregate-functions-entity-sql"></a>聚合函数 (Entity SQL)
聚合是一种语言构造，它将集合浓缩为标量以作为组运算的一部分。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 聚合分为两种形式：  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 可能在表达式中任何位置使用的集合函数。 这包括在作用于集合的投影和谓词中使用聚合函数。 集合函数是在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中指定聚合的首选模式。  
  
-   具有 GROUP BY 子句的表达式中的组聚合。 与在 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 中一样，组聚合接受 DISTINCT 和 ALL 作为聚合输入的修饰符。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 首先尝试将解释为集合函数的表达式，如果表达式为 SELECT 表达式的上下文中它将其解释为组聚合。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 定义特殊的聚合运算符，称为[GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md)。 此运算符，您可以获得对分组的输入集的引用。 这样，就可以进行更高级的分组查询，其中，GROUP BY 子句的结果可以用在除组聚合或集合函数之外的位置。  
  
## <a name="collection-functions"></a>集合函数  
 集合函数针对集合运行并返回标量值。 例如，如果 `orders` 是所有 `orders` 的集合，则可以使用以下表达式计算最早的发货日期：  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>组聚合  
 组聚合将按照 GROUP BY 子句定义的方式对组结果进行计算。 GROUP BY 子句将数据分区为组。 对于结果中的每个组，将应用聚合函数，并使用每个组中的元素作为聚合计算的输入来计算单独的聚合。 当在 SELECT 表达式中使用 GROUP BY 子句时，在投影、HAVING 或 ORDER BY 子句中只能存在分组表达式名称、聚合或常量表达式。  
  
 以下示例计算每种产品的平均订购数量。  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 在 SELECT 表达式中，可以在没有显式 GROUP BY 子句的情况下使用组聚合。 所有元素均将被视为单个组，这等同于基于常量指定分组的情况。  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 将使用 WHERE 子句表达式可见的相同名称解析范围计算 GROUP BY 子句中使用的表达式。  
  
## <a name="see-also"></a>请参阅

- [函数](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
