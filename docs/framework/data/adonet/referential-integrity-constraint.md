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
# <a name="referential-integrity-constraint"></a><span data-ttu-id="7adbe-103">引用完整性约束</span><span class="sxs-lookup"><span data-stu-id="7adbe-103">referential integrity constraint</span></span>
<span data-ttu-id="7adbe-104">实体数据模型（EDM）中的*引用完整性约束*类似于关系数据库中的引用完整性约束。</span><span class="sxs-lookup"><span data-stu-id="7adbe-104">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="7adbe-105">与数据库表中的列（或列）可以引用另一个表的主键相同，[实体类型](entity-type.md)的一个或多个[属性](property.md)可以引用另一个实体类型的[实体键](entity-key.md)。</span><span class="sxs-lookup"><span data-stu-id="7adbe-105">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](property.md) (or properties) of an [entity type](entity-type.md) can reference the [entity key](entity-key.md) of another entity type.</span></span> <span data-ttu-id="7adbe-106">引用的实体类型称为约束的*主体端*。</span><span class="sxs-lookup"><span data-stu-id="7adbe-106">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="7adbe-107">引用主体端的实体类型称为约束的*依赖端*。</span><span class="sxs-lookup"><span data-stu-id="7adbe-107">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="7adbe-108">引用完整性约束定义为两个实体类型之间的[关联](association-type.md)的一部分。</span><span class="sxs-lookup"><span data-stu-id="7adbe-108">A referential integrity constraint is defined as part of an [association](association-type.md) between two entity types.</span></span> <span data-ttu-id="7adbe-109">引用完整性约束的定义指定了以下信息：</span><span class="sxs-lookup"><span data-stu-id="7adbe-109">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
- <span data-ttu-id="7adbe-110">约束的主体端。</span><span class="sxs-lookup"><span data-stu-id="7adbe-110">The principal end of the constraint.</span></span> <span data-ttu-id="7adbe-111">（一个实体类型，其实体键由依赖端引用。）</span><span class="sxs-lookup"><span data-stu-id="7adbe-111">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
- <span data-ttu-id="7adbe-112">主体端的实体键。</span><span class="sxs-lookup"><span data-stu-id="7adbe-112">The entity key of the principal end.</span></span>  
  
- <span data-ttu-id="7adbe-113">约束的依赖端。</span><span class="sxs-lookup"><span data-stu-id="7adbe-113">The dependent end of the constraint.</span></span> <span data-ttu-id="7adbe-114">（一个实体类型，它的一个或多个属性引用主体端的实体键。）</span><span class="sxs-lookup"><span data-stu-id="7adbe-114">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
- <span data-ttu-id="7adbe-115">依赖端的一个或多个引用属性。</span><span class="sxs-lookup"><span data-stu-id="7adbe-115">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="7adbe-116">EDM 中的引用完整性约束的用途是确保始终存在有效关联。</span><span class="sxs-lookup"><span data-stu-id="7adbe-116">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="7adbe-117">有关详细信息，请参阅[外键属性](foreign-key-property.md)。</span><span class="sxs-lookup"><span data-stu-id="7adbe-117">For more information, see [foreign key property](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7adbe-118">示例</span><span class="sxs-lookup"><span data-stu-id="7adbe-118">Example</span></span>  
 <span data-ttu-id="7adbe-119">下图显示了一个具有两个关联的概念模型：`WrittenBy` 和 `PublishedBy`。</span><span class="sxs-lookup"><span data-stu-id="7adbe-119">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="7adbe-120">`Book` 实体类型有一个属性 `PublisherId`，当您为 `Publisher` 关联定义一个引用完整性约束时，它将引用 `PublishedBy` 实体类型的实体键。</span><span class="sxs-lookup"><span data-stu-id="7adbe-120">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="7adbe-121">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "引用约束模型的示例")</span><span class="sxs-lookup"><span data-stu-id="7adbe-121">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="7adbe-122">[ADO.NET 实体框架](./ef/index.md)使用一种称为概念架构定义语言（[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)）的域特定语言（DSL）来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="7adbe-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="7adbe-123">下面的 CSDL 为上图所示的概念模型中的 `PublishedBy` 关联定义了一个引用完整性约束。</span><span class="sxs-lookup"><span data-stu-id="7adbe-123">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="7adbe-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7adbe-124">See also</span></span>

- [<span data-ttu-id="7adbe-125">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="7adbe-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="7adbe-126">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="7adbe-126">Entity Data Model</span></span>](entity-data-model.md)
