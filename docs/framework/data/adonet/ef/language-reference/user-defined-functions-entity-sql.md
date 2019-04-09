---
title: 用户定义的函数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 4922e7fada676a6c26042236ccdb6315d6d455ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104619"
---
# <a name="user-defined-functions-entity-sql"></a>用户定义的函数 (Entity SQL)
Entity SQL 支持在查询中调用用户定义函数。 您可以定义与查询这些函数内联 (请参阅[如何：调用用户定义的函数](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) 或为概念模型的一部分 (请参阅[如何：概念模型中定义自定义函数](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)))。 概念模型函数定义为中的 Entity SQL 命令[DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl)的元素[函数](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl)概念模型中的元素。  
  
 通过 Entity SQL，您可以在查询命令自身中定义函数。 [函数](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)运算符定义内联函数。 您可以在单个命令中定义多个函数，这些函数可以具有相同的函数名称，只要函数签名是唯一的。 有关详细信息，请参阅 [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)。  
  
## <a name="see-also"></a>请参阅

- [函数](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
