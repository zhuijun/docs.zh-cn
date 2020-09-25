---
title: 对象标识
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
ms.openlocfilehash: 1a1617b4fb15a6adf94c0241c3ba577308c51a8b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169422"
---
# <a name="object-identity"></a><span data-ttu-id="900ed-102">对象标识</span><span class="sxs-lookup"><span data-stu-id="900ed-102">Object Identity</span></span>

<span data-ttu-id="900ed-103">运行库中的对象具有唯一标识。</span><span class="sxs-lookup"><span data-stu-id="900ed-103">Objects in the runtime have unique identities.</span></span> <span data-ttu-id="900ed-104">引用同一对象的两个变量实际上是引用此对象的同一实例。</span><span class="sxs-lookup"><span data-stu-id="900ed-104">Two variables that refer to the same object actually refer to the same instance of the object.</span></span> <span data-ttu-id="900ed-105">因为这一事实，您通过一个变量做出更改后，立即就可以通过另一个变量看到这些更改。</span><span class="sxs-lookup"><span data-stu-id="900ed-105">Because of this fact, changes that you make by way of a path through one variable are immediately visible through the other.</span></span>  
  
 <span data-ttu-id="900ed-106">关系数据库表中的行不具有唯一标识。</span><span class="sxs-lookup"><span data-stu-id="900ed-106">Rows in a relational database table do not have unique identities.</span></span> <span data-ttu-id="900ed-107">由于每一行都具有唯一的主键，因此任何两行都不会共用同一键值。</span><span class="sxs-lookup"><span data-stu-id="900ed-107">Because each row has a unique primary key, no two rows share the same key value.</span></span> <span data-ttu-id="900ed-108">但是，这一事实仅限于数据库表的内容。</span><span class="sxs-lookup"><span data-stu-id="900ed-108">However, this fact constrains only the contents of the database table.</span></span>  
  
 <span data-ttu-id="900ed-109">实际上，通常都是将数据从数据库中提取出来放入另一层中，应用程序在该层对数据进行处理。</span><span class="sxs-lookup"><span data-stu-id="900ed-109">In reality, data is most often brought out of the database and into a different tier, where an application works with it.</span></span> <span data-ttu-id="900ed-110">这就是 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支持的模型。</span><span class="sxs-lookup"><span data-stu-id="900ed-110">This is the model that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports.</span></span> <span data-ttu-id="900ed-111">将数据作为行从数据库中提取出来时，您不期望表示相同数据的两行实际上对应于相同的行实例。</span><span class="sxs-lookup"><span data-stu-id="900ed-111">When data is brought out of the database as rows, you have no expectation that two rows that represent the same data actually correspond to the same row instances.</span></span> <span data-ttu-id="900ed-112">如果您查询特定客户两次，您将获得两行数据。</span><span class="sxs-lookup"><span data-stu-id="900ed-112">If you query for a specific customer two times, you get two rows of data.</span></span> <span data-ttu-id="900ed-113">每一行包含相同的信息。</span><span class="sxs-lookup"><span data-stu-id="900ed-113">Each row contains the same information.</span></span>  
  
 <span data-ttu-id="900ed-114">对于对象，您的期望则大不一样。</span><span class="sxs-lookup"><span data-stu-id="900ed-114">With objects you expect something very different.</span></span> <span data-ttu-id="900ed-115">您期望在您反复向 <xref:System.Data.Linq.DataContext> 索取相同的信息时，它实际上会为您提供同一对象实例。</span><span class="sxs-lookup"><span data-stu-id="900ed-115">You expect that if you ask the <xref:System.Data.Linq.DataContext> for the same information repeatedly, it will in fact give you the same object instance.</span></span> <span data-ttu-id="900ed-116">您之所以期望这种行为，是因为对象对您的应用程序而言有着特殊的含义，您期望它们的行为像实物一样。</span><span class="sxs-lookup"><span data-stu-id="900ed-116">You expect this behavior because objects have special meaning for your application and you expect them to behave like objects.</span></span> <span data-ttu-id="900ed-117">您将它们设计为层次结构或关系图。</span><span class="sxs-lookup"><span data-stu-id="900ed-117">You designed them as hierarchies or graphs.</span></span> <span data-ttu-id="900ed-118">您希望像检索实物一样检索它们，而不希望仅仅因为您多次索要同一内容而收到大量的复制实例。</span><span class="sxs-lookup"><span data-stu-id="900ed-118">You expect to retrieve them as such and not to receive multitudes of replicated instances just because you asked for the same thing more than one time.</span></span>  
  
 <span data-ttu-id="900ed-119">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Data.Linq.DataContext> 管理对象标识。</span><span class="sxs-lookup"><span data-stu-id="900ed-119">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.DataContext> manages object identity.</span></span> <span data-ttu-id="900ed-120">只要您从数据库中检索新行，该行就会由其主键记录到标识表中，并且会创建一个新的对象。</span><span class="sxs-lookup"><span data-stu-id="900ed-120">Whenever you retrieve a new row from the database, the row is logged in an identity table by its primary key, and a new object is created.</span></span> <span data-ttu-id="900ed-121">只要您检索该行，就会将原始对象实例传递回应用程序。</span><span class="sxs-lookup"><span data-stu-id="900ed-121">Whenever you retrieve that same row, the original object instance is handed back to the application.</span></span> <span data-ttu-id="900ed-122">通过这种方式，<xref:System.Data.Linq.DataContext> 将数据库看到的标识（即主键）的概念转换成相应语言看到的标识（即实例）的概念。</span><span class="sxs-lookup"><span data-stu-id="900ed-122">In this manner the <xref:System.Data.Linq.DataContext> translates the concept of identity as seen by the database (that is, primary keys) into the concept of identity seen by the language (that is, instances).</span></span> <span data-ttu-id="900ed-123">应用程序只看到处于第一次检索时的状态的对象。</span><span class="sxs-lookup"><span data-stu-id="900ed-123">The application only sees the object in the state that it was first retrieved.</span></span> <span data-ttu-id="900ed-124">新数据如果不同，则会被丢弃。</span><span class="sxs-lookup"><span data-stu-id="900ed-124">The new data, if different, is discarded.</span></span> <span data-ttu-id="900ed-125">有关详细信息，请参阅 [从标识缓存中检索对象](retrieving-objects-from-the-identity-cache.md)。</span><span class="sxs-lookup"><span data-stu-id="900ed-125">For more information, see [Retrieving Objects from the Identity Cache](retrieving-objects-from-the-identity-cache.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="900ed-126">使用此方法来管理本地对象的完整性，以支持开放式更新。</span><span class="sxs-lookup"><span data-stu-id="900ed-126">uses this approach to manage the integrity of local objects in order to support optimistic updates.</span></span> <span data-ttu-id="900ed-127">由于在最初创建对象后唯一发生的更改是由应用程序做出的，因此应用程序的意向是很明确的。</span><span class="sxs-lookup"><span data-stu-id="900ed-127">Because the only changes that occur after the object is at first created are those made by the application, the intent of the application is clear.</span></span> <span data-ttu-id="900ed-128">如果在中间阶段外部某一方做了更改，则在调用 `SubmitChanges()` 时会识别出这些更改。</span><span class="sxs-lookup"><span data-stu-id="900ed-128">If changes by an outside party have occurred in the interim, they are identified at the time `SubmitChanges()` is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="900ed-129">如果查询请求的对象易被识别为已检索到的对象，则不会执行查询。</span><span class="sxs-lookup"><span data-stu-id="900ed-129">If the object requested by the query is easily identifiable as one already retrieved, no query is executed.</span></span> <span data-ttu-id="900ed-130">标识表用作以前检索到的所有对象的缓存。</span><span class="sxs-lookup"><span data-stu-id="900ed-130">The identity table acts as a cache of all previously retrieved objects.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="900ed-131">示例</span><span class="sxs-lookup"><span data-stu-id="900ed-131">Examples</span></span>  
  
### <a name="object-caching-example-1"></a><span data-ttu-id="900ed-132">对象缓存示例 1</span><span class="sxs-lookup"><span data-stu-id="900ed-132">Object Caching Example 1</span></span>  

 <span data-ttu-id="900ed-133">在此示例中，如果您执行同一查询两次，则您每次都会收到对内存中同一对象的引用。</span><span class="sxs-lookup"><span data-stu-id="900ed-133">In this example, if you execute the same query two times, you receive a reference to the same object in memory every time.</span></span>  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a><span data-ttu-id="900ed-134">对象缓存示例 2</span><span class="sxs-lookup"><span data-stu-id="900ed-134">Object Caching Example 2</span></span>  

 <span data-ttu-id="900ed-135">在此示例中，如果您执行返回数据库中同一行的不同查询，则您每次都会收到对内存中同一对象的引用。</span><span class="sxs-lookup"><span data-stu-id="900ed-135">In this example, if you execute different queries that return the same row from the database, you receive a reference to the same object in memory every time.</span></span>  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="900ed-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="900ed-136">See also</span></span>

- [<span data-ttu-id="900ed-137">背景信息</span><span class="sxs-lookup"><span data-stu-id="900ed-137">Background Information</span></span>](background-information.md)
