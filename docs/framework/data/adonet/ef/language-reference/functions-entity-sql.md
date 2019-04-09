---
title: 函数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: f31f829b53160da5a043617b9aa999b398859f17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080600"
---
# <a name="functions-entity-sql"></a>函数 (Entity SQL)
Entity SQL 支持用户定义函数、规范函数和提供程序特定的函数。 用户定义函数在概念模型中指定，或在查询中内联指定。 有关详细信息，请参阅[用户定义的函数](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)。  
  
 在实体框架中对规范函数进行了预定义，因此数据提供程序将支持规范函数。 如果用户调用提供程序不支持的函数，则 Entity SQL 命令将失败。 因此，通常建议使用规范函数而不是存储特定的函数，后者位于提供程序特定的命名空间中。 有关详细信息，请参阅[规范函数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)。  
  
 Microsoft SQL 客户端托管访问接口提供了一组提供程序特定的函数。 有关详细信息，请参阅[用于实体框架函数的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [用户定义的函数](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [函数重载解析](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [聚合函数](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>请参阅

- [Entity SQL 概述](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
