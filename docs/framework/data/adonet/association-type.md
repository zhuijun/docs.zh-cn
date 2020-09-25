---
title: 关联类型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 6f6eb91d4f292c7e98b8c9a1d814ed6bf71b7370
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198751"
---
# <a name="association-type"></a><span data-ttu-id="2fadf-102">关联类型</span><span class="sxs-lookup"><span data-stu-id="2fadf-102">association type</span></span>

<span data-ttu-id="2fadf-103">*关联类型* (也称为关联) 是用于描述实体数据模型 (EDM) 中的关系的基本构造块。</span><span class="sxs-lookup"><span data-stu-id="2fadf-103">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="2fadf-104">在概念模型中，关联表示两个 [实体类型](entity-type.md) 之间的关系 (例如 `Customer` 和 `Order`) 。</span><span class="sxs-lookup"><span data-stu-id="2fadf-104">In a conceptual model, an association represents a relationship between two [entity types](entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="2fadf-105">在应用程序中，一个关联实例表示一个特定的关联（例如 `Customer` 实例与 `Order` 实例之间的关联）。</span><span class="sxs-lookup"><span data-stu-id="2fadf-105">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="2fadf-106">关联实例按逻辑分组到一个 [关联集](association-set.md)。</span><span class="sxs-lookup"><span data-stu-id="2fadf-106">Association instances are logically grouped in an [association set](association-set.md).</span></span>  
  
 <span data-ttu-id="2fadf-107">关联定义包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="2fadf-107">An association definition contains the following information:</span></span>  
  
- <span data-ttu-id="2fadf-108">唯一名称。</span><span class="sxs-lookup"><span data-stu-id="2fadf-108">A unique name.</span></span> <span data-ttu-id="2fadf-109">（必需）</span><span class="sxs-lookup"><span data-stu-id="2fadf-109">(Required)</span></span>  
  
- <span data-ttu-id="2fadf-110">两个 [关联结束](association-end.md)，关系中的每个实体类型都有一个。</span><span class="sxs-lookup"><span data-stu-id="2fadf-110">Two [association ends](association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="2fadf-111">（必需）</span><span class="sxs-lookup"><span data-stu-id="2fadf-111">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2fadf-112">关联不能表示两个以上的实体类型之间的关系。</span><span class="sxs-lookup"><span data-stu-id="2fadf-112">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="2fadf-113">但是，通过为每个关联端指定相同的实体类型，关联可以定义自身关系。</span><span class="sxs-lookup"><span data-stu-id="2fadf-113">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
- <span data-ttu-id="2fadf-114">[引用完整性约束](referential-integrity-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="2fadf-114">A [referential integrity constraint](referential-integrity-constraint.md).</span></span> <span data-ttu-id="2fadf-115">(可选)</span><span class="sxs-lookup"><span data-stu-id="2fadf-115">(Optional)</span></span>  
  
 <span data-ttu-id="2fadf-116">每个关联端都必须指定一个 [关联端多重性](association-end-multiplicity.md) ，以指示可以位于关联一端的实体类型实例的数量。</span><span class="sxs-lookup"><span data-stu-id="2fadf-116">Each association end must specify an [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="2fadf-117">关联 end 多重性的值可以是 1) 、零或 1 (0 () 或多个 (\*) 。</span><span class="sxs-lookup"><span data-stu-id="2fadf-117">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="2fadf-118">可以通过 [导航属性](navigation-property.md) 或外键（如果在实体类型上公开）来访问关联一端的实体类型实例。</span><span class="sxs-lookup"><span data-stu-id="2fadf-118">Entity type instances at one end of an association can be accessed through [navigation properties](navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="2fadf-119">有关详细信息，请参阅 [实体数据模型：外键](foreign-key-property.md)。</span><span class="sxs-lookup"><span data-stu-id="2fadf-119">For more information, see [Entity Data Model: Foreign Keys](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fadf-120">示例</span><span class="sxs-lookup"><span data-stu-id="2fadf-120">Example</span></span>  

 <span data-ttu-id="2fadf-121">下图显示了一个具有两个关联的概念模型：`PublishedBy` 和 `WrittenBy`。</span><span class="sxs-lookup"><span data-stu-id="2fadf-121">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="2fadf-122">`PublishedBy` 关联的关联端是 `Book` 和 `Publisher` 实体类型。</span><span class="sxs-lookup"><span data-stu-id="2fadf-122">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="2fadf-123">末尾的重数 `Publisher` 为一 (1) ，结束的重数 `Book` 为许多 (\*) ，这表示发布者发布了许多书籍，书籍发布了一个出版商。</span><span class="sxs-lookup"><span data-stu-id="2fadf-123">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![具有三个实体类型的示例模型](./media/association-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="2fadf-125">[ADO.NET 实体框架](./ef/index.md)使用一种特定于域的语言 (DSL) 称为概念架构定义语言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="2fadf-125">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="2fadf-126">下面的 CSDL 定义了上图中显示的 `PublishedBy` 关联：</span><span class="sxs-lookup"><span data-stu-id="2fadf-126">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="2fadf-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="2fadf-127">See also</span></span>

- [<span data-ttu-id="2fadf-128">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="2fadf-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="2fadf-129">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="2fadf-129">Entity Data Model</span></span>](entity-data-model.md)
