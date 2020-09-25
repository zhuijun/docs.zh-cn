---
title: 实体集
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 6286d3707a8506e7a389359a5aa361c152e75212
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194786"
---
# <a name="entity-set"></a><span data-ttu-id="8b0f4-102">实体集</span><span class="sxs-lookup"><span data-stu-id="8b0f4-102">entity set</span></span>

<span data-ttu-id="8b0f4-103">*实体集*是某个[实体类型](entity-type.md)的实例和从该实体类型派生的任何类型的实例的逻辑容器。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-103">An *entity set* is a logical container for instances of an [entity type](entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="8b0f4-104"> (有关派生类型的信息，请参阅 [实体数据模型：继承](entity-data-model-inheritance.md)。 ) 实体类型与实体集之间的关系类似于关系数据库中行与表之间的关系：与行相同，实体类型描述数据结构，而与表一样，实体集包含给定结构的实例。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-104">(For information about derived types, see [Entity Data Model: Inheritance](entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="8b0f4-105">实体集不是一种数据建模构造，它没有描述数据结构。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="8b0f4-106">相反，实体集提供了一种承载或存储环境构造（例如公共语言运行库或 SQL Server 数据库）来分组实体类型实例，以便可以将它们映射到某个数据存储区。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="8b0f4-107">实体集是在 [实体容器](entity-container.md)中定义的，实体容器是实体集和 [关联集](association-set.md)的逻辑分组。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-107">An entity set is defined within an [entity container](entity-container.md), which is a logical grouping of entity sets and [association sets](association-set.md).</span></span>  
  
 <span data-ttu-id="8b0f4-108">对于实体集中存在的实体类型实例，必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="8b0f4-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
- <span data-ttu-id="8b0f4-109">实例的类型或者与实体集所基于的实体类型相同，或者是该实体类型的一个子类型。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
- <span data-ttu-id="8b0f4-110">实例的 [实体键](entity-key.md) 在实体集内是唯一的。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-110">The [entity key](entity-key.md) for the instance is unique within the entity set.</span></span>  
  
- <span data-ttu-id="8b0f4-111">实例不存在于任何其他实体集中。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8b0f4-112">可以使用相同的实体类型定义多个实体集，但某个给定实体类型的一个实例只能存在于一个实体集中。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="8b0f4-113">不必为概念模型中的每个实体类型都定义实体集。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b0f4-114">示例</span><span class="sxs-lookup"><span data-stu-id="8b0f4-114">Example</span></span>  

 <span data-ttu-id="8b0f4-115">下图显示了一个具有三个实体类型的概念模型：`Book`、`Publisher` 和 `Author`。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![具有三个实体类型的示例模型](./media/entity-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="8b0f4-117">下图显示了基于上面所示的概念模型的两个实体集（`Books` 和 `Publishers`）和一个关联集 (`PublishedBy`)。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="8b0f4-118">`Books`实体集中的 Bi 表示 `Book` 运行时实体类型的实例。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="8b0f4-119">同样，Pj 表示 `Publisher` 实体集中的实例 `Publishers` 。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="8b0f4-120">BiPj 表示 `PublishedBy` 关联集中关联的实例 `PublishedBy` 。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![显示集合示例的屏幕截图。](./media/entity-set/sets-example-association.gif)  
  
 <span data-ttu-id="8b0f4-122">[ADO.NET 实体框架](./ef/index.md)使用一种特定于域的语言 (DSL) 称为概念架构定义语言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="8b0f4-123">下面的 CSDL 定义了一个实体容器，其中对于上图所示的概念模型中的每个实体类型都有一个实体集。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="8b0f4-124">请注意，每个实体集的名称和实体类型都是使用 XML 特性定义的。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="8b0f4-125">每个类型可以定义多个实体集 (MEST)。</span><span class="sxs-lookup"><span data-stu-id="8b0f4-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="8b0f4-126">下面的 CSDL 定义了一个实体容器，其中包含 `Book` 实体类型的两个实体集：</span><span class="sxs-lookup"><span data-stu-id="8b0f4-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="8b0f4-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="8b0f4-127">See also</span></span>

- [<span data-ttu-id="8b0f4-128">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="8b0f4-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="8b0f4-129">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="8b0f4-129">Entity Data Model</span></span>](entity-data-model.md)
