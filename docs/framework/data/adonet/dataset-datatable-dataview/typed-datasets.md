---
title: 类型化数据集
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 92ed3f8fd392238785fd2d205668f14fe477f2b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098645"
---
# <a name="typed-datasets"></a>类型化数据集
在允许通过弱类型化变量对值进行后期绑定访问的同时，<xref:System.Data.DataSet> 还允许通过强类型化比喻对数据进行访问。 表和列的一部分**数据集**可以使用用户友好的名称来访问和强类型化变量。  
  
 类型化**数据集**是派生一个类**数据集**。 在这种情况下，它将继承所有方法、 事件和属性的**数据集**。 此外，类型化**数据集**提供强类型的方法、 事件和属性。 这意味着可以按名称（而不是使用基于集合的方法）访问表和列。 除了改进的类型化的代码可读性**数据集**还允许 Visual Studio.NET 代码编辑器中键入时自动完成的行。  
  
 此外，强类型**数据集**提供对正确类型在编译时对值的访问。 使用强类型化**数据集**，当代码是编译而不是在运行时捕获类型不匹配错误。  
  
## <a name="in-this-section"></a>本节内容  
 [生成强类型化数据集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 介绍如何创建和使用强类型化**数据集**。  
  
 [为类型化的数据集进行批注](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 描述如何批注 XML 架构定义语言 (XSD) 架构用于生成强类型化**数据集**，以便**数据集**元素友好的名称，而无需更改基础架构。  
  
## <a name="see-also"></a>请参阅

- [数据集、数据表和数据视图](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
