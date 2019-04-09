---
title: 自定义操作：概述
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: 29fb75271b7bc324d462078e94e4a28534986fba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075972"
---
# <a name="customizing-operations-overview"></a>自定义操作：概述
默认情况下，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会根据映射生成动态 SQL 来执行插入、更新和删除操作。 但在实践中，您通常需要添加您自己的业务逻辑来提供安全、验证等。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 自定义这些操作的方法包括以下内容。  
  
## <a name="loading-options"></a>加载选项  
 在您的查询中，您可以控制在连接到数据库时检索多少与您的主目标相关的数据。 此功能主要通过使用 <xref:System.Data.Linq.DataLoadOptions> 实现。 有关详细信息，请参阅[推迟加载与即时加载](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)。  
  
## <a name="partial-methods"></a>分部方法  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在其默认映射中提供了分部方法，以帮助您实现自己的业务逻辑。 有关详细信息，请参阅[添加业务逻辑通过使用分部方法](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)。  
  
## <a name="stored-procedures-and-user-defined-functions"></a>存储过程和用户定义的函数  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支持使用存储的过程和用户定义的函数。 存储过程经常用来自定义操作。 有关详细信息，请参阅[存储过程](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)。  
  
## <a name="see-also"></a>请参阅

- [自定义插入、更新和删除操作](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
