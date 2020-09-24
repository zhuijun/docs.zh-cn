---
title: 关联端重数
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cf9e6b5af0dc6a33af364901c631b4ce66fe0480
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153503"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="658c3-102">关联端重数</span><span class="sxs-lookup"><span data-stu-id="658c3-102">association end multiplicity</span></span>

<span data-ttu-id="658c3-103">*关联 end 多重性*定义可以位于[关联](association-type.md)一端的[实体类型](entity-type.md)实例的数量。</span><span class="sxs-lookup"><span data-stu-id="658c3-103">*Association end multiplicity* defines the number of [entity type](entity-type.md) instances that can be at one end of an [association](association-type.md).</span></span>  
  
 <span data-ttu-id="658c3-104">关联端重数可以具有下列值之一：</span><span class="sxs-lookup"><span data-stu-id="658c3-104">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="658c3-105">一 (1)：表明在关联端存在且只存在一个实体类型实例。</span><span class="sxs-lookup"><span data-stu-id="658c3-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="658c3-106">零或一 (0..1)：表明在关联端不存在实体类型实例或存在一个实体类型实例。</span><span class="sxs-lookup"><span data-stu-id="658c3-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="658c3-107">许多 (\*) ：指示在关联端存在零个、一个或多个实体类型实例。</span><span class="sxs-lookup"><span data-stu-id="658c3-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="658c3-108">关联的特征通常由关联端重数表示。</span><span class="sxs-lookup"><span data-stu-id="658c3-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="658c3-109">例如，如果关联的两端有一个 (1) 和多个 (\*) 的重数，则该关联称为一对多关联。</span><span class="sxs-lookup"><span data-stu-id="658c3-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="658c3-110">在下面的示例中，`PublishedBy` 关联是一个一对多关联（一个出版商可以出版很多书，而一本书只能由一个出版商出版）。</span><span class="sxs-lookup"><span data-stu-id="658c3-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="658c3-111">`WrittenBy` 关联是一个多对多关联（一本书可以有多位作者，而一位作者可以著有多本书）。</span><span class="sxs-lookup"><span data-stu-id="658c3-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="658c3-112">示例</span><span class="sxs-lookup"><span data-stu-id="658c3-112">Example</span></span>  

 <span data-ttu-id="658c3-113">下图显示了一个具有两个关联的概念模型：`PublishedBy` 和 `WrittenBy`。</span><span class="sxs-lookup"><span data-stu-id="658c3-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="658c3-114">`PublishedBy` 关联的关联端是 `Book` 和 `Publisher` 实体类型。</span><span class="sxs-lookup"><span data-stu-id="658c3-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="658c3-115">末尾的重数 `Publisher` 为 1 (1) ，结束的重数 `Book` 为多 (\*) 。</span><span class="sxs-lookup"><span data-stu-id="658c3-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![具有三个实体类型的示例模型](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="658c3-117">ADO.NET 实体框架使用一种特定于域的语言 (DSL) 称为概念架构定义语言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="658c3-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="658c3-118">下面的 CSDL 定义了上图中显示的 `PublishedBy` 关联：</span><span class="sxs-lookup"><span data-stu-id="658c3-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="658c3-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="658c3-119">See also</span></span>

- [<span data-ttu-id="658c3-120">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="658c3-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="658c3-121">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="658c3-121">Entity Data Model</span></span>](entity-data-model.md)
