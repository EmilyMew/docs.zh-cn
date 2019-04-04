---
title: 实体数据模型关键概念
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: bcfc9cbb82a23dcb4d33ca8a838a49eac7180111
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825659"
---
# <a name="entity-data-model-key-concepts"></a>实体数据模型关键概念
实体数据模型 (EDM) 使用三个关键概念来描述数据结构：*实体类型*，*关联类型*，并*属性*。 在任何 EDM 实现中，这些都是描述数据结构的最重要概念。  
  
## <a name="entity-type"></a>实体类型  
 [实体类型](../../../../docs/framework/data/adonet/entity-type.md)是用于描述实体数据模型的数据结构的基本构建块。 在概念模型中，实体类型从构造[属性](../../../../docs/framework/data/adonet/property.md)和描述结构的顶级概念，如客户和订单的业务应用程序中。 正如计算机程序中的类定义是用于类实例的模板一样，实体类型也是实体的模板。 实体表示一个特定对象（例如特定的客户或订单）。 每个实体都必须具有一个唯一[实体键](../../../../docs/framework/data/adonet/entity-key.md)内[实体集](../../../../docs/framework/data/adonet/entity-set.md)。  实体集是指特定实体类型的实例集合。 实体集 (和[关联集](../../../../docs/framework/data/adonet/association-set.md)) 按逻辑分组在[实体容器](../../../../docs/framework/data/adonet/entity-container.md)。  
  
 实体类型支持继承功能：即一个实体类型可以从另一个实体类型中派生。 有关详细信息，请参阅[实体数据模型：继承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)。  
  
## <a name="association-type"></a>关联类型  
 [关联类型](../../../../docs/framework/data/adonet/association-type.md)（也称为关联） 是用于描述实体数据模型中的关系的基本构建块。 在概念模型中，关联表示两个实体类型（例如 Customer 和 Order）之间的关系。 每个关联具有两个[关联端](../../../../docs/framework/data/adonet/association-end.md)，用于指定关联中涉及的实体类型。 每个关联端还指定了[关联端重数](../../../../docs/framework/data/adonet/association-end-multiplicity.md)，该值指示该关联端处可以存在的实体数。 关联端重数的值可以为“一 (1)”、“零或一 (0..1)”或“多 (*)”。 可以通过访问的关联某一端的实体[导航属性](../../../../docs/framework/data/adonet/navigation-property.md)，或如果在实体类型上公开了外键。 有关详细信息，请参阅[外键属性](../../../../docs/framework/data/adonet/foreign-key-property.md)。  
  
 在应用程序中，关联实例表示特定的关联（例如 Customer 实例与 Order 实例之间的关联）。 关联实例按逻辑分组在[关联集](../../../../docs/framework/data/adonet/association-set.md)。 关联集 (和[实体集](../../../../docs/framework/data/adonet/entity-set.md)) 按逻辑分组在[实体容器](../../../../docs/framework/data/adonet/entity-container.md)。  
  
## <a name="property"></a>属性  
 [实体类型](../../../../docs/framework/data/adonet/entity-type.md)包含[属性](../../../../docs/framework/data/adonet/property.md)用于定义其结构和特征。 例如，Customer 实体类型可能具有 CustomerId、Name 及 Address 这样的属性。  
  
 概念模型中的属性类似于对计算机程序中的类所定义的属性。 正如类的属性定义类的形状和携带有关对象的信息一样，概念模型中的属性也定义实体类型的形状和携带有关实体类型实例的信息。  
  
 属性可以包含基元数据（例如字符串、整数或布尔值）或结构化数据（例如复杂类型）。 有关详细信息，请参阅[实体数据模型：基元数据类型](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)。  
  
## <a name="representations-of-a-conceptual-model"></a>概念模型的表示形式  
 一个*概念模型*是为实体和关系的特定表示形式的一些数据结构。 概念模型的一种表示形式是图表。 下图用三个实体类型（`Book`、`Publisher` 和 `Author`）以及两个关联（`PublishedBy` 和 `WrittenBy`）来表示概念模型：  
  
 ![显示具有三个实体类型的概念模型关系图。](./media/entity-data-model-key-concepts/conceptual-model-entity-types-associations.gif)  
  
 然而，如果要传达一些有关模型的详细信息，这种表现形式存在一些不足。 例如，图中没有传达属性类型和实体集信息。 域特定语言 (DSL) 可用于更明确地传达有关概念模型的大量信息。 [ADO.NET 实体框架](../../../../docs/framework/data/adonet/ef/index.md)使用名为基于 XML 的 DSL*概念架构定义语言*([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 来定义概念模型。 下面是上图所示的概念模型的 CSDL 定义。  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>请参阅
- [实体数据模型](../../../../docs/framework/data/adonet/entity-data-model.md)
