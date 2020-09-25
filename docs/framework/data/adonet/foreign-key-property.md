---
title: 外键属性
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: be0fcb94b0b457a33c17e7125cd22db50f298cc6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189313"
---
# <a name="foreign-key-property"></a><span data-ttu-id="2af0b-102">外键属性</span><span class="sxs-lookup"><span data-stu-id="2af0b-102">foreign key property</span></span>

<span data-ttu-id="2af0b-103">实体数据模型 (EDM) 中的*外键属性*是一个基元类型[属性](property.md)， (或一组基元类型属性) 在包含另一个实体类型的[实体键](entity-key.md)的[实体类型](entity-type.md)上。</span><span class="sxs-lookup"><span data-stu-id="2af0b-103">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](property.md) (or a set of primitive type properties) on an [entity type](entity-type.md) that contains the [entity key](entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="2af0b-104">外键属性相当于关系数据库中的外键列。</span><span class="sxs-lookup"><span data-stu-id="2af0b-104">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="2af0b-105">与在关系数据库中使用外键列来创建表中各行之间的关系一样，概念模型中的外键属性用于建立实体类型之间的 [关联](association-type.md) 。</span><span class="sxs-lookup"><span data-stu-id="2af0b-105">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](association-type.md) between entity types.</span></span> <span data-ttu-id="2af0b-106">当一个类型具有外键属性时， [引用完整性约束](referential-integrity-constraint.md) 用于定义两个实体类型之间的关联。</span><span class="sxs-lookup"><span data-stu-id="2af0b-106">A [referential integrity constraint](referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2af0b-107">示例</span><span class="sxs-lookup"><span data-stu-id="2af0b-107">Example</span></span>  

 <span data-ttu-id="2af0b-108">下图显示了一个具有三个实体类型的概念模型：`Book`、`Publisher` 和 `Author`。</span><span class="sxs-lookup"><span data-stu-id="2af0b-108">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="2af0b-109">`Book` 实体类型有一个属性 `PublisherId`，当您为 `Publisher` 关联定义一个引用完整性约束时，它将引用 `PublishedBy` 实体类型的实体键。</span><span class="sxs-lookup"><span data-stu-id="2af0b-109">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="2af0b-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "引用约束模型的示例")</span><span class="sxs-lookup"><span data-stu-id="2af0b-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="2af0b-111">[ADO.NET 实体框架](./ef/index.md)使用一种特定于域的语言 (DSL) 称为概念架构定义语言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="2af0b-111">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="2af0b-112">下面的 CSDL 使用外键属性 `PublisherId` 为上图所示的概念模型中的 `PublishedBy` 关联定义了一个引用完整性约束。</span><span class="sxs-lookup"><span data-stu-id="2af0b-112">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="2af0b-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="2af0b-113">See also</span></span>

- [<span data-ttu-id="2af0b-114">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="2af0b-114">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="2af0b-115">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="2af0b-115">Entity Data Model</span></span>](entity-data-model.md)
