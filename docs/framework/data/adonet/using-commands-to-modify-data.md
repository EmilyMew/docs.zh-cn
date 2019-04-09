---
title: 使用命令修改数据
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: f2e3d162bfbdcb79cfecefa4ddc8e6a0dc46ee3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102448"
---
# <a name="using-commands-to-modify-data"></a>使用命令修改数据
使用 .NET Framework 数据提供程序，您可以执行存储过程或数据定义语言语句（如 CREATE TABLE 和 ALTER COLUMN）来对数据库或编录执行架构处理。 这些命令不返回行像查询一样，因此**命令**对象提供**ExecuteNonQuery**来处理它们。  
  
 除了使用之外**ExecuteNonQuery**来修改架构，您可以使用过程的 SQL 语句修改数据，但不是返回行，如 INSERT、 UPDATE，并删除此方法。  
  
 虽然不返回行**ExecuteNonQuery**方法、 输入和输出参数和返回值可以传递并通过返回**参数**的集合**命令**对象。  
  
## <a name="in-this-section"></a>本节内容  
 [更新数据源中的数据](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 描述如何执行对数据库中的数据进行修改的命令或存储过程。  
  
 [执行目录操作](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 描述如何执行对数据库架构进行修改的命令。  
  
## <a name="see-also"></a>请参阅

- [在 ADO.NET 中检索和修改数据](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [命令和参数](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
