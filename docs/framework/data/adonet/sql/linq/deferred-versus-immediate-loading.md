---
title: 推迟加载与即时加载
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
ms.openlocfilehash: 4e2cb7c90eb703985cbb1b8673522a9e253564d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164293"
---
# <a name="deferred-versus-immediate-loading"></a><span data-ttu-id="c5e64-102">推迟加载与即时加载</span><span class="sxs-lookup"><span data-stu-id="c5e64-102">Deferred versus Immediate Loading</span></span>

<span data-ttu-id="c5e64-103">查询某对象时，实际上您只检索请求的对象。</span><span class="sxs-lookup"><span data-stu-id="c5e64-103">When you query for an object, you actually retrieve only the object you requested.</span></span> <span data-ttu-id="c5e64-104">不会同时自动提取 *相关* 的对象。</span><span class="sxs-lookup"><span data-stu-id="c5e64-104">The *related* objects are not automatically fetched at the same time.</span></span> <span data-ttu-id="c5e64-105"> (有关详细信息，请参阅 [跨关系进行查询](querying-across-relationships.md)。 ) 找不到相关对象尚未加载的事实，因为尝试访问它们会生成检索它们的请求。</span><span class="sxs-lookup"><span data-stu-id="c5e64-105">(For more information, see [Querying Across Relationships](querying-across-relationships.md).) You cannot see the fact that the related objects are not already loaded, because an attempt to access them produces a request that retrieves them.</span></span>  
  
 <span data-ttu-id="c5e64-106">例如，你可能需要查询一组特定的订单，然后仅偶尔向特定客户发送电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="c5e64-106">For example, you might want to query for a particular set of orders and then only occasionally send an email notification to particular customers.</span></span> <span data-ttu-id="c5e64-107">您最初不一定需要检索与每个订单有关的所有客户数据。</span><span class="sxs-lookup"><span data-stu-id="c5e64-107">You would not necessarily need initially to retrieve all customer data with every order.</span></span> <span data-ttu-id="c5e64-108">您可以使用延迟加载将额外信息的检索操作延迟到您确实需要检索它们时再进行。</span><span class="sxs-lookup"><span data-stu-id="c5e64-108">You can use deferred loading to defer retrieval of extra information until you absolutely have to.</span></span> <span data-ttu-id="c5e64-109">请考虑以下示例：</span><span class="sxs-lookup"><span data-stu-id="c5e64-109">Consider the following example:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 <span data-ttu-id="c5e64-110">反过来也可能是可行的。</span><span class="sxs-lookup"><span data-stu-id="c5e64-110">The opposite might also be true.</span></span> <span data-ttu-id="c5e64-111">您的应用程序可能必须同时查看客户数据和订单数据。</span><span class="sxs-lookup"><span data-stu-id="c5e64-111">You might have an application that has to view customer and order data at the same time.</span></span> <span data-ttu-id="c5e64-112">您了解同时需要这两组数据。</span><span class="sxs-lookup"><span data-stu-id="c5e64-112">You know you need both sets of data.</span></span> <span data-ttu-id="c5e64-113">您了解一旦获得结果，您的应用程序就需要每个客户的订单信息。</span><span class="sxs-lookup"><span data-stu-id="c5e64-113">You know your application needs order information for each customer as soon as you get the results.</span></span> <span data-ttu-id="c5e64-114">您不希望一个一个地提交对每个客户的订单的查询。</span><span class="sxs-lookup"><span data-stu-id="c5e64-114">You would not want to submit individual queries for orders for every customer.</span></span> <span data-ttu-id="c5e64-115">您真正想要的是将订单数据与客户信息一起检索出来。</span><span class="sxs-lookup"><span data-stu-id="c5e64-115">What you really want is to retrieve the order data together with the customers.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 <span data-ttu-id="c5e64-116">您还可以在查询中联接客户和订单，方法是构建叉积并将所有相关数据位作为一个大型投影检索出来。</span><span class="sxs-lookup"><span data-stu-id="c5e64-116">You can also join customers and orders in a query by forming the cross-product and retrieving all the relative bits of data as one large projection.</span></span> <span data-ttu-id="c5e64-117">但这些结果并非实体。</span><span class="sxs-lookup"><span data-stu-id="c5e64-117">But these results are not entities.</span></span> <span data-ttu-id="c5e64-118">有关详细信息，请参阅 [LINQ to SQL 对象模型) 的](the-linq-to-sql-object-model.md) (。</span><span class="sxs-lookup"><span data-stu-id="c5e64-118">(For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md)).</span></span> <span data-ttu-id="c5e64-119">实体是具有标识且您可以修改的对象，而这些结果将是无法更改和持久化的投影。</span><span class="sxs-lookup"><span data-stu-id="c5e64-119">Entities are objects that have identity and that you can modify, whereas these results would be projections that cannot be changed and persisted.</span></span> <span data-ttu-id="c5e64-120">更糟的是，您将检索到大量的冗余数据，因为在平展联接输出中，对于每个订单，每个客户将重复出现。</span><span class="sxs-lookup"><span data-stu-id="c5e64-120">Even worse, you would be retrieving lots of redundant data as each customer repeats for each order in the flattened join output.</span></span>  
  
 <span data-ttu-id="c5e64-121">您真正需要的是同时检索相关对象的集合的方法。</span><span class="sxs-lookup"><span data-stu-id="c5e64-121">What you really need is a way to retrieve a set of related objects at the same time.</span></span> <span data-ttu-id="c5e64-122">此集合是关系图的精确剖面，因此您检索到的数据绝不会比您所需要的数据多或少。</span><span class="sxs-lookup"><span data-stu-id="c5e64-122">The set is a delineated section of a graph so that you would never be retrieving more or less than was necessary for your intended use.</span></span> <span data-ttu-id="c5e64-123">为此，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提供了 <xref:System.Data.Linq.DataLoadOptions>，用以立即加载对象模型的某一区域。</span><span class="sxs-lookup"><span data-stu-id="c5e64-123">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides <xref:System.Data.Linq.DataLoadOptions> for immediate loading of a region of your object model.</span></span> <span data-ttu-id="c5e64-124">方法包括：</span><span class="sxs-lookup"><span data-stu-id="c5e64-124">Methods include:</span></span>  
  
- <span data-ttu-id="c5e64-125"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> 方法，用于立即加载与主目标相关的数据。</span><span class="sxs-lookup"><span data-stu-id="c5e64-125">The  <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method, to immediately load data related to the main target.</span></span>  
  
- <span data-ttu-id="c5e64-126"><xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 方法，用于筛选为特定关系检索到的对象。</span><span class="sxs-lookup"><span data-stu-id="c5e64-126">The <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method, to filter objects retrieved for a particular relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e64-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="c5e64-127">See also</span></span>

- [<span data-ttu-id="c5e64-128">查询概念</span><span class="sxs-lookup"><span data-stu-id="c5e64-128">Query Concepts</span></span>](query-concepts.md)
