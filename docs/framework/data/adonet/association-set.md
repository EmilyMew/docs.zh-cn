---
title: Association Set — 关联集
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: 2eaa4d3c70e0efbf9705b4285d1abd4753bd1db9
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411260"
---
# <a name="association-set"></a>Association Set — 关联集
*关联集*是逻辑容器[关联](../../../../docs/framework/data/adonet/association-type.md)相同类型的实例。 关联集不是一种数据建模构造，也就是说，它没有描述数据结构或关系。 相反，关联集提供了一种承载或存储环境构造（例如公共语言运行库或 SQL Server 数据库）来分组关联实例，以便可以将它们映射到某个数据存储区。  
  
 关联集定义中[实体容器](../../../../docs/framework/data/adonet/entity-container.md)，即的逻辑分组[实体集](../../../../docs/framework/data/adonet/entity-set.md)和关联集。  
  
 关联集的定义包含以下信息：  
  
-   关联集名称。 （必需）  
  
-   要包含其实例的关联。 （必需）  
  
-   两个[关联集端](../../../../docs/framework/data/adonet/association-set-end.md)。  
  
## <a name="example"></a>示例  
 下图显示了一个具有两个关联的概念模型：`PublishedBy` 和 `WrittenBy`。 上图没有传达有关关联集的信息，但下图显示了一个基于此模型的关联集和实体集的示例。  
  
 ![具有三个实体类型的示例模型](./media/association-set/example-model-three-entity-types.gif)  
  
 下面的示例显示了基于上面所示的概念模型的一个关联集 (`PublishedBy`) 和两个实体集（`Books` 和 `Publishers`）。 在 bi`Books`实体集表示的实例`Book`实体类型，在运行时。 同样，表示 Pj`Publisher`实例中`Publishers`实体集。 BiPj 表示的实例`PublishedBy`中的关联`PublishedBy`关联集。  
  
 ![显示设置示例的屏幕截图。](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET 实体框架](../../../../docs/framework/data/adonet/ef/index.md)使用称为概念性架构定义语言的特定于域的语言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 来定义概念模型。 下面的 CSDL 定义了一个实体容器，其中对于上图所示的每个关联都有一个关联集。 请注意，每个关联集的名称和关联都是使用 XML 特性定义的。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 可以定义每个关联，只要没有两个关联集共享的多个关联集[关联集端](../../../../docs/framework/data/adonet/association-set-end.md)。 下面的 CSDL 定义了一个实体容器，其中包含 `WrittenBy` 关联的两个关联集。 请注意，为 `Book` 和 `Author` 实体类型定义了多个实体集，并且没有关联集共享关联集端。  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>请参阅
- [实体数据模型关键概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [实体数据模型](../../../../docs/framework/data/adonet/entity-data-model.md)
- [外键属性](../../../../docs/framework/data/adonet/foreign-key-property.md)
