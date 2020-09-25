---
title: 跨关系查询
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: 24ab13a1d67eac39c7b3d7be8cb1c16ec7265d5e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184872"
---
# <a name="querying-across-relationships"></a><span data-ttu-id="f0c9b-102">跨关系查询</span><span class="sxs-lookup"><span data-stu-id="f0c9b-102">Querying Across Relationships</span></span>

<span data-ttu-id="f0c9b-103">您的类定义中对其他对象或其他对象的集合的直接引用相当于数据库中的外键关系。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-103">References to other objects or collections of other objects in your class definitions directly correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="f0c9b-104">您可以通过使用点表示法在查询时利用这些关系来访问关系属性以及从一个对象定位到另一个对象。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-104">You can use these relationships when you query by using dot notation to access the relationship properties and navigate from one object to another.</span></span> <span data-ttu-id="f0c9b-105">这些访问操作会转换成用等效的 SQL 表示的更为复杂的联接或关联子查询。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-105">These access operations translate to more complex joins or correlated subqueries in the equivalent SQL.</span></span>  
  
 <span data-ttu-id="f0c9b-106">例如，下面的查询从订单定位到客户，以此方式将结果限制为只包括位于伦敦的客户的订单。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-106">For example, the following query navigates from orders to customers as a way to restrict the results to only those orders for customers located in London.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 <span data-ttu-id="f0c9b-107">如果关系属性不存在，则必须以 *联接*的形式手动编写它们，就像在 SQL 查询中那样，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="f0c9b-107">If relationship properties did not exist you would have to write them manually as *joins*, just as you would do in a SQL query, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 <span data-ttu-id="f0c9b-108">您可以使用 " *关系* " 属性一次定义此特定关系。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-108">You can use the *relationship* property to define this particular relationship one time.</span></span> <span data-ttu-id="f0c9b-109">然后您就可以使用更为方便的点语法。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-109">You can then use the more convenient dot syntax.</span></span> <span data-ttu-id="f0c9b-110">但之所以存在关系属性，更重要的原因在于特定于域的对象模型通常定义为层次结构或关系图。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-110">But relationship properties exist more importantly because domain-specific object models are typically defined as hierarchies or graphs.</span></span> <span data-ttu-id="f0c9b-111">您要进行编程的那些对象引用其他对象。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-111">The objects that you program against have references to other objects.</span></span> <span data-ttu-id="f0c9b-112">如果对象与对象的关系相当于数据库中外键类型的关系，那么这只是一种令人庆幸的巧合而已。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-112">It is only a happy coincidence that object-to-object relationships correspond to foreign-key-styled relationships in databases.</span></span> <span data-ttu-id="f0c9b-113">在这种情况下，可以很方便地通过访问属性来编写联接。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-113">Property access then provides a convenient way to write joins.</span></span>  
  
 <span data-ttu-id="f0c9b-114">就这一点而言，关系属性在查询的结果方面要比作为查询本身的一部分重要。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-114">With regard to this, relationship properties are more important on the results side of a query than as part of the query itself.</span></span> <span data-ttu-id="f0c9b-115">在查询检索到关于特定客户的数据后，类定义会指示客户下了订单。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-115">After the query has retrieved data about a particular customer, the class definition indicates that customers have orders.</span></span> <span data-ttu-id="f0c9b-116">换言之，您希望特定客户的 `Orders` 属性是用该客户下的所有订单填充的集合。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-116">In other words, you expect the `Orders` property of a particular customer to be a collection that is populated with all the orders from that customer.</span></span> <span data-ttu-id="f0c9b-117">这实际上是您通过以此方式定义类声明的协定。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-117">That is in fact the contract you declared by defining the classes in this manner.</span></span> <span data-ttu-id="f0c9b-118">即便查询并未请求订单，您也希望在那里看到这些订单。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-118">You expect to see the orders there even if the query did not request orders.</span></span> <span data-ttu-id="f0c9b-119">您希望自己的对象模型保持这样的错觉：它是数据库在内存中的扩展，并且相关对象立即可用。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-119">You expect your object model to maintain an illusion that it is an in-memory extension of the database with related objects immediately available.</span></span>  
  
 <span data-ttu-id="f0c9b-120">既然您已经具备了关系，您就可以通过引用您的类中定义的关系属性来编写查询。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-120">Now that you have relationships, you can write queries by referring to the relationship properties defined in your classes.</span></span> <span data-ttu-id="f0c9b-121">这些关系引用相当于数据库中的外键关系。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-121">These relationship references correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="f0c9b-122">使用这些关系的操作会转换成用等效的 SQL 表示的更为复杂的联接。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-122">Operations that use these relationships translate to more complex joins in the equivalent SQL.</span></span> <span data-ttu-id="f0c9b-123">只要你已经定义关系（使用 <xref:System.Data.Linq.Mapping.AssociationAttribute> 属性），你就无需在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中编写显式联接的代码。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-123">As long as you have defined a relationship (using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute), you do not have to code an explicit join in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="f0c9b-124">为了帮助保持这种错觉， [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 实现了一种称为 *延迟加载*的技术。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-124">To help maintain this illusion, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implements a technique called *deferred loading*.</span></span> <span data-ttu-id="f0c9b-125">有关详细信息，请参阅 [延迟与立即加载](deferred-versus-immediate-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-125">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
 <span data-ttu-id="f0c9b-126">请考虑以下 SQL 查询来投影对的列表 `CustomerID` - `OrderID` ：</span><span class="sxs-lookup"><span data-stu-id="f0c9b-126">Consider the following SQL query to project a list of `CustomerID`-`OrderID` pairs:</span></span>  
  
```sql
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 <span data-ttu-id="f0c9b-127">若要通过使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 获得相同的结果，您可以使用 `Orders` 类中已经存在的 `Customer` 属性引用。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-127">To obtain the same results by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the `Orders` property reference already existing in the `Customer` class.</span></span> <span data-ttu-id="f0c9b-128">`Orders`引用提供了执行查询和投影对所需的信息 `CustomerID` - `OrderID` ，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="f0c9b-128">The `Orders` reference provides the necessary information to execute the query and project the `CustomerID`-`OrderID` pairs, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 <span data-ttu-id="f0c9b-129">您也可以反向操作。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-129">You can also do the reverse.</span></span> <span data-ttu-id="f0c9b-130">也就是说，您可以查询 `Orders`，然后使用其 `Customer` 关系引用来访问关于关联的 `Customer` 对象的信息。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-130">That is, you can query `Orders` and use its `Customer` relationship reference to access information about the associated `Customer` object.</span></span> <span data-ttu-id="f0c9b-131">下面的代码将与之前相同的对进行投影 `CustomerID` - `OrderID` ，但这一次是通过查询 `Orders` 而不是 `Customers` 。</span><span class="sxs-lookup"><span data-stu-id="f0c9b-131">The following code projects the same `CustomerID`-`OrderID` pairs as before, but this time by querying `Orders` instead of `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="f0c9b-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="f0c9b-132">See also</span></span>

- [<span data-ttu-id="f0c9b-133">查询概念</span><span class="sxs-lookup"><span data-stu-id="f0c9b-133">Query Concepts</span></span>](query-concepts.md)
