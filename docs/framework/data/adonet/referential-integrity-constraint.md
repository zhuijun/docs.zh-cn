---
title: 引用完整性约束
description: 了解实体数据模型中的引用完整性约束，该约束确保实体类型之间始终存在有效的关联。
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 65c811b2a12a64870107ff771d5acc64e86f2c1f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286619"
---
# <a name="referential-integrity-constraint"></a>引用完整性约束
实体数据模型（EDM）中的*引用完整性约束*类似于关系数据库中的引用完整性约束。 与数据库表中的列（或列）可以引用另一个表的主键相同，[实体类型](entity-type.md)的一个或多个[属性](property.md)可以引用另一个实体类型的[实体键](entity-key.md)。 引用的实体类型称为约束的*主体端*。 引用主体端的实体类型称为约束的*依赖端*。  
  
 引用完整性约束定义为两个实体类型之间的[关联](association-type.md)的一部分。 引用完整性约束的定义指定了以下信息：  
  
- 约束的主体端。 （一个实体类型，其实体键由依赖端引用。）  
  
- 主体端的实体键。  
  
- 约束的依赖端。 （一个实体类型，它的一个或多个属性引用主体端的实体键。）  
  
- 依赖端的一个或多个引用属性。  
  
 EDM 中的引用完整性约束的用途是确保始终存在有效关联。 有关详细信息，请参阅[外键属性](foreign-key-property.md)。  
  
## <a name="example"></a>示例  
 下图显示了一个具有两个关联的概念模型：`WrittenBy` 和 `PublishedBy`。 `Book` 实体类型有一个属性 `PublisherId`，当您为 `Publisher` 关联定义一个引用完整性约束时，它将引用 `PublishedBy` 实体类型的实体键。  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "引用约束模型的示例")  
  
 [ADO.NET 实体框架](./ef/index.md)使用一种称为概念架构定义语言（[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)）的域特定语言（DSL）来定义概念模型。 下面的 CSDL 为上图所示的概念模型中的 `PublishedBy` 关联定义了一个引用完整性约束。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>另请参阅

- [实体数据模型关键概念](entity-data-model-key-concepts.md)
- [实体数据模型](entity-data-model.md)
