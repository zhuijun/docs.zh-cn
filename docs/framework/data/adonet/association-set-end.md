---
title: 关联集端
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: bd104ffb46cbd02a886ce87822ddc37159961174
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198790"
---
# <a name="association-set-end"></a><span data-ttu-id="0a0c2-102">关联集端</span><span class="sxs-lookup"><span data-stu-id="0a0c2-102">association set end</span></span>

<span data-ttu-id="0a0c2-103">*关联集端*在[关联集](association-set.md)的末尾标识[实体类型](entity-type.md)和[实体集](entity-set.md)。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-103">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="0a0c2-104">关联集端定义为关联集的一部分；一个关联集必须有且只有两个关联集端。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="0a0c2-105">关联集端定义包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="0a0c2-105">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="0a0c2-106">关联集中涉及的实体类型之一。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="0a0c2-107">（必需）</span><span class="sxs-lookup"><span data-stu-id="0a0c2-107">(Required)</span></span>  
  
- <span data-ttu-id="0a0c2-108">关联集中涉及的实体类型的实体集。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="0a0c2-109">（必需）</span><span class="sxs-lookup"><span data-stu-id="0a0c2-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a0c2-110">示例</span><span class="sxs-lookup"><span data-stu-id="0a0c2-110">Example</span></span>  

 <span data-ttu-id="0a0c2-111">下图显示了一个具有两个关联的概念模型：`WrittenBy` 和 `PublishedBy`。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![具有三个实体类型的示例模型](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="0a0c2-113">下图显示了基于上面所示的概念模型的一个关联集 (`PublishedBy`) 和两个实体集（`Books` 和 `Publishers`）。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="0a0c2-114">关联集端是 `Books` 和 `Publishers` 实体集。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="0a0c2-115">`Books`实体集中的 Bi 表示 `Book` 运行时实体类型的实例。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="0a0c2-116">同样，Pj 表示 `Publisher` 实体集中的实例 `Publishers` 。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="0a0c2-117">BiPj 表示 `PublishedBy` 关联集中关联的实例 `PublishedBy` 。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![显示集合示例的屏幕截图。](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="0a0c2-119">[ADO.NET 实体框架](./ef/index.md)使用称为概念架构定义语言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 的 DSL 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-119">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="0a0c2-120">下面的 CSDL 定义了一个实体容器，其中对于上图所示的每个关联都有一个关联集。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="0a0c2-121">请注意，关联集端定义为每个关联集定义的一部分。</span><span class="sxs-lookup"><span data-stu-id="0a0c2-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="0a0c2-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="0a0c2-122">See also</span></span>

- [<span data-ttu-id="0a0c2-123">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="0a0c2-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="0a0c2-124">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="0a0c2-124">Entity Data Model</span></span>](entity-data-model.md)
