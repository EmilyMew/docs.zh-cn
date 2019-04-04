---
title: 关联类型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 895d7fdc464741723322717c3ace027dc49eed9c
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411442"
---
# <a name="association-type"></a>关联类型
*关联类型*（也称为关联） 是用于描述实体数据模型 (EDM) 中的关系的基本构建块。 在概念模型中，关联表示两个之间的关系[实体类型](../../../../docs/framework/data/adonet/entity-type.md)(如`Customer`和`Order`)。 在应用程序中，一个关联实例表示一个特定的关联（例如 `Customer` 实例与 `Order` 实例之间的关联）。 关联实例按逻辑分组在[关联集](../../../../docs/framework/data/adonet/association-set.md)。  
  
 关联定义包含以下信息：  
  
-   唯一名称。 （必需）  
  
-   两个[关联端](../../../../docs/framework/data/adonet/association-end.md)，一个用于在关系中每个实体类型。 （必需）  
  
    > [!NOTE]
    >  关联不能表示两个以上的实体类型之间的关系。 但是，通过为每个关联端指定相同的实体类型，关联可以定义自身关系。  
  
-   一个[引用完整性约束](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)。 （可选）  
  
 每个关联端必须指定[关联端重数](../../../../docs/framework/data/adonet/association-end-multiplicity.md)，该值指示关联的一端可以存在的实体类型实例数。 关联端重数可以具有值为一 (1) 零或一 (0..1) 或许多 (\*)。 可以通过访问实体类型实例的关联某一端[导航属性](../../../../docs/framework/data/adonet/navigation-property.md)或如果在实体类型上公开了外键。 有关详细信息，请参阅[实体数据模型：外键](../../../../docs/framework/data/adonet/foreign-key-property.md)。  
  
## <a name="example"></a>示例  
 下图显示了一个具有两个关联的概念模型：`PublishedBy` 和 `WrittenBy`。 
  `PublishedBy` 关联的关联端是 `Book` 和 `Publisher` 实体类型。 多重性`Publisher`最终为一 (1) 和重数`Book`最终为多个 (\*)，指示，出版商可以出版很多书而一本书只能由一个出版商出版。  
  
 ![具有三个实体类型的示例模型](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET 实体框架](../../../../docs/framework/data/adonet/ef/index.md)使用称为概念性架构定义语言的特定于域的语言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 来定义概念模型。 下面的 CSDL 定义了上图中显示的 `PublishedBy` 关联：  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>请参阅

- [实体数据模型关键概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [实体数据模型](../../../../docs/framework/data/adonet/entity-data-model.md)
