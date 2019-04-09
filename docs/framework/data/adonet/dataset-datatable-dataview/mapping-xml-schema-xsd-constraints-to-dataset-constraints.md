---
title: 将关键 XML 架构 (XSD) 约束映射到数据集约束
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: a1690e99aeaeb7ed9c85fd28697ae22d34bb2018
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115643"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>将关键 XML 架构 (XSD) 约束映射到数据集约束
XML 架构定义语言 (XSD) 允许对它所定义的元素和属性指定约束。 映射到关系架构中的 XML 架构时<xref:System.Data.DataSet>，XML 架构约束将映射到上的表和列中的相应关系约束**数据集**。  
  
 本节讨论以下 XML 架构约束的映射：  
  
-   使用指定的唯一性约束**唯一**元素。  
  
-   使用指定的键约束**密钥**元素。  
  
-   使用指定的 keyref 约束**keyref**元素。  
  
 使用对元素或属性的约束，可以对任何文档实例中元素的值指定特定的限制。 例如上, 一个键约束**CustomerID**的子元素**客户**架构中的元素指示的值**CustomerID**子元素必须为在任何文档实例中唯一，不允许 null 值。  
  
 为了在文档中建立关系，也可以在文档中的元素和属性之间指定约束。 key 和 keyref 约束用于在架构中指定文档中的约束，从而生成文档元素和属性之间的关系。  
  
 映射过程将这些架构约束转换中创建的表上的相应约束**数据集**。  
  
## <a name="in-this-section"></a>本节内容  
 [将唯一 XML 架构 (XSD) 约束映射到数据集约束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用于创建唯一约束中的 XML 架构元素**数据集**。  
  
 [将关键 XML 架构 (XSD) 约束映射到数据集约束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用于创建键约束 （唯一约束不允许空值） 的 XML 架构元素中**数据集**。  
  
 [将 keyref XML 架构 (XSD) 约束映射到数据集约束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用于创建 keyref （外键） 约束中的 XML 架构元素**数据集**。  
  
## <a name="related-sections"></a>相关章节  
 [从 XML 架构派生数据集关系结构 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 描述的关系结构或架构**数据集**创建从 XSD 架构。  
  
 [从 XML 架构生成数据集关系 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 描述用于创建表中的列之间的关系的 XML 架构元素**数据集**。  
  
## <a name="see-also"></a>请参阅

- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
