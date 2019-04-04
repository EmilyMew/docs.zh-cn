---
title: 关联集端
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 61dc00e6c349a25767f6221bed56ef8b65f823d9
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412001"
---
# <a name="association-set-end"></a>关联集端
*关联集端*标识[实体类型](../../../../docs/framework/data/adonet/entity-type.md)并[实体集](../../../../docs/framework/data/adonet/entity-set.md)末尾[关联集](../../../../docs/framework/data/adonet/association-set.md)。 关联集端定义为关联集的一部分；一个关联集必须有且只有两个关联集端。  
  
 关联集端定义包含以下信息：  
  
-   关联集中涉及的实体类型之一。 （必需）  
  
-   关联集中涉及的实体类型的实体集。 （必需）  
  
## <a name="example"></a>示例  
 下图显示了一个具有两个关联的概念模型：`WrittenBy` 和 `PublishedBy`。  
  
 ![具有三个实体类型的示例模型](./media/association-set-end/example-model-three-entity-types.gif)  
  
 下图显示了基于上面所示的概念模型的一个关联集 (`PublishedBy`) 和两个实体集（`Books` 和 `Publishers`）。 关联集端是 `Books` 和 `Publishers` 实体集。 在 bi`Books`实体集表示的实例`Book`实体类型，在运行时。 同样，表示 Pj`Publisher`实例中`Publishers`实体集。 BiPj 表示的实例`PublishedBy`中的关联`PublishedBy`关联集。  
  
 ![显示设置示例的屏幕截图。](./media/association-set-end/sets-example-association.gif)  
  
 [ADO.NET 实体框架](../../../../docs/framework/data/adonet/ef/index.md)使用 DSL 称为概念架构定义语言 ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 来定义概念模型。 下面的 CSDL 定义了一个实体容器，其中对于上图所示的每个关联都有一个关联集。 请注意，关联集端定义为每个关联集定义的一部分。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>请参阅
- [实体数据模型关键概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [实体数据模型](../../../../docs/framework/data/adonet/entity-data-model.md)
