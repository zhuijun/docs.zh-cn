---
title: N 层应用程序中的数据检索和 CUD 操作 (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: 1bc97504b4dd053ce9ef747460a79865cbe836ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197412"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="c0252-102">N 层应用程序中的数据检索和 CUD 操作 (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="c0252-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>

<span data-ttu-id="c0252-103">在将实体对象（如 Customers 或 Orders）通过网络序列化到客户端时，这些实体会与其数据上下文分离。</span><span class="sxs-lookup"><span data-stu-id="c0252-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="c0252-104">数据上下文不再跟踪这些实体的更改或它们与其他对象的关联。</span><span class="sxs-lookup"><span data-stu-id="c0252-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="c0252-105">只要客户端只读取数据，这就不会成为问题。</span><span class="sxs-lookup"><span data-stu-id="c0252-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="c0252-106">要使客户端可以向数据库添加新行，也比较容易做到。</span><span class="sxs-lookup"><span data-stu-id="c0252-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="c0252-107">但是，如果应用程序要求客户端能够更新或删除数据，则必须在调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType> 之前将实体附加到新的数据上下文。</span><span class="sxs-lookup"><span data-stu-id="c0252-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c0252-108">此外，如果对原始值使用开放式并发检查，则还需要一种为数据库同时提供原始实体和修改后的实体的方式。</span><span class="sxs-lookup"><span data-stu-id="c0252-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="c0252-109">使用 `Attach` 方法可以在实体分离后将其放入新的数据上下文中。</span><span class="sxs-lookup"><span data-stu-id="c0252-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="c0252-110">即使要序列化代理对象来代替 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 实体，仍然必须在数据访问层 (DAL) 上构造一个实体，并将其附加到新的 <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>，以便将数据提交给数据库。</span><span class="sxs-lookup"><span data-stu-id="c0252-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c0252-111">完全不关心实体的序列化方式。</span><span class="sxs-lookup"><span data-stu-id="c0252-111">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="c0252-112">有关如何使用对象关系设计器和 SQLMetal 工具生成可通过 Windows Communication Foundation (WCF) 进行序列化的类的详细信息，请参阅 [如何：使实体可序列化](how-to-make-entities-serializable.md)。</span><span class="sxs-lookup"><span data-stu-id="c0252-112">For more information about how to use the Object Relational Designer and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0252-113">仅对新实体或反序列化后的实体调用 `Attach` 方法。</span><span class="sxs-lookup"><span data-stu-id="c0252-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="c0252-114">将实体与其原始数据上下文分离的唯一方式是将其序列化。</span><span class="sxs-lookup"><span data-stu-id="c0252-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="c0252-115">如果试图将未分离的实体附加到新的数据上下文，并且该实体仍然具有来自其以前的数据上下文的延迟加载程序，则 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会引发异常。</span><span class="sxs-lookup"><span data-stu-id="c0252-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="c0252-116">如果一个实体具有来自两个不同数据上下文的延迟加载程序，则在对该实体执行插入、更新和删除操作时，可能产生意外的结果。</span><span class="sxs-lookup"><span data-stu-id="c0252-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="c0252-117">有关延迟加载程序的详细信息，请参阅 [延迟与立即加载](deferred-versus-immediate-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="c0252-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="c0252-118">检索数据</span><span class="sxs-lookup"><span data-stu-id="c0252-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="c0252-119">客户端方法调用</span><span class="sxs-lookup"><span data-stu-id="c0252-119">Client Method Call</span></span>  

 <span data-ttu-id="c0252-120">下面的示例演示一个从 Windows 窗体客户端对 DAL 进行的示例方法调用。</span><span class="sxs-lookup"><span data-stu-id="c0252-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="c0252-121">在此示例中，DAL 被实现为 Windows 服务库：</span><span class="sxs-lookup"><span data-stu-id="c0252-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
```vb  
Private Function GetProdsByCat_Click(ByVal sender As Object, ByVal e _  
    As EventArgs)  
  
    ' Create the WCF client proxy.  
    Dim proxy As New NorthwindServiceReference.Service1Client  
  
    ' Call the method on the service.  
    Dim products As NorthwindServiceReference.Product() = _  
        proxy.GetProductsByCategory(1)  
  
    ' If the database uses original values for concurrency checks,  
    ' the client needs to store them and pass them back to the  
    ' middle tier along with the new values when updating data.  
  
    For Each v As NorthwindClient1.NorthwindServiceReference.Product _  
        In products  
        ' Persist to a List(Of Product) declared at class scope.  
        ' Additional change-tracking logic is the responsibility  
        ' of the presentation tier and/or middle tier.  
        originalProducts.Add(v)  
    Next  
  
    ' (Not shown) Bind the products list to a control  
    ' and/or perform whatever processing is necessary.  
End Function  
```  
  
```csharp  
private void GetProdsByCat_Click(object sender, EventArgs e)  
{  
    // Create the WCF client proxy.  
    NorthwindServiceReference.Service1Client proxy =
    new NorthwindClient.NorthwindServiceReference.Service1Client();  
  
    // Call the method on the service.  
    NorthwindServiceReference.Product[] products =
    proxy.GetProductsByCategory(1);  
  
    // If the database uses original values for concurrency checks,
    // the client needs to store them and pass them back to the
    // middle tier along with the new values when updating data.  
    foreach (var v in products)  
    {  
        // Persist to a list<Product> declared at class scope.  
        // Additional change-tracking logic is the responsibility  
        // of the presentation tier and/or middle tier.  
        originalProducts.Add(v);  
    }  
  
    // (Not shown) Bind the products list to a control  
    // and/or perform whatever processing is necessary.  
    }  
```  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="c0252-122">中间层实现</span><span class="sxs-lookup"><span data-stu-id="c0252-122">Middle Tier Implementation</span></span>  

 <span data-ttu-id="c0252-123">下面的示例演示中间层上的接口方法的实现。</span><span class="sxs-lookup"><span data-stu-id="c0252-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="c0252-124">下面是要注意的两个要点：</span><span class="sxs-lookup"><span data-stu-id="c0252-124">The following are the two main points to note:</span></span>  
  
- <span data-ttu-id="c0252-125"><xref:System.Data.Linq.DataContext> 是在方法范围上声明的。</span><span class="sxs-lookup"><span data-stu-id="c0252-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
- <span data-ttu-id="c0252-126">该方法返回实际结果的 <xref:System.Collections.IEnumerable> 集合。</span><span class="sxs-lookup"><span data-stu-id="c0252-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="c0252-127">序列化程序将执行查询，以便将结果发送回客户端/表示层。</span><span class="sxs-lookup"><span data-stu-id="c0252-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="c0252-128">若要在中间层上对查询结果进行本地访问，可以通过对查询变量调用 `ToList` 或 `ToArray` 来强制执行。</span><span class="sxs-lookup"><span data-stu-id="c0252-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="c0252-129">然后，可以将该列表或数组作为 `IEnumerable` 返回。</span><span class="sxs-lookup"><span data-stu-id="c0252-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
```vb  
Public Function GetProductsByCategory(ByVal categoryID As Integer) _  
    As IEnumerable(Of Product)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    Dim productQuery = _  
    From prod In db.Products _  
    Where prod.CategoryID = categoryID _  
    Select prod  
  
    Return productQuery.AsEnumerable()  
  
End Function  
```  
  
```csharp  
public IEnumerable<Product> GetProductsByCategory(int categoryID)  
{  
    NorthwindClasses1DataContext db =
    new NorthwindClasses1DataContext(connectionString);  
  
    IEnumerable<Product> productQuery =  
    from prod in db.Products  
    where prod.CategoryID == categoryID  
    select prod;  
  
    return productQuery.AsEnumerable();
}  
```  
  
 <span data-ttu-id="c0252-130">数据上下文的实例应具有一个“工作单元”的生存期。</span><span class="sxs-lookup"><span data-stu-id="c0252-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="c0252-131">在松耦合环境中，工作单元通常较小，它可能是一个开放式事务，其中包含对 `SubmitChanges` 的单个调用。</span><span class="sxs-lookup"><span data-stu-id="c0252-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="c0252-132">因此，数据上下文在方法范围上创建和释放。</span><span class="sxs-lookup"><span data-stu-id="c0252-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="c0252-133">如果工作单元包含对业务规则逻辑的调用，则通常需要为整个操作保持 `DataContext` 实例。</span><span class="sxs-lookup"><span data-stu-id="c0252-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="c0252-134">在任何情况下，都不应该使 `DataContext` 实例在任意数量的事务之间长时间保持活动状态。</span><span class="sxs-lookup"><span data-stu-id="c0252-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="c0252-135">此方法会返回 Product 对象，但不会返回与每个 Product 相关联的 Order_Detail 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="c0252-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="c0252-136">使用 <xref:System.Data.Linq.DataLoadOptions> 对象可以更改此默认行为。</span><span class="sxs-lookup"><span data-stu-id="c0252-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="c0252-137">有关详细信息，请参阅 [如何：控制检索的相关数据量](how-to-control-how-much-related-data-is-retrieved.md)。</span><span class="sxs-lookup"><span data-stu-id="c0252-137">For more information, see [How to: Control How Much Related Data Is Retrieved](how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="c0252-138">插入数据</span><span class="sxs-lookup"><span data-stu-id="c0252-138">Inserting Data</span></span>  

 <span data-ttu-id="c0252-139">为了插入新对象，表示层只是调用中间层接口上的相关方法，并传入要插入的新对象。</span><span class="sxs-lookup"><span data-stu-id="c0252-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="c0252-140">在某些情况下，对于客户端而言，仅传入一些值并让中间层来构造完整对象可能更加高效。</span><span class="sxs-lookup"><span data-stu-id="c0252-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="c0252-141">中间层实现</span><span class="sxs-lookup"><span data-stu-id="c0252-141">Middle Tier Implementation</span></span>  

 <span data-ttu-id="c0252-142">在中间层上，创建一个新的 <xref:System.Data.Linq.DataContext>，使用 <xref:System.Data.Linq.DataContext> 方法将该对象附加到 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>，并在调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时插入该对象。</span><span class="sxs-lookup"><span data-stu-id="c0252-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="c0252-143">异常、回调和错误条件可以像在任何其他 Web 服务方案中一样进行处理。</span><span class="sxs-lookup"><span data-stu-id="c0252-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
```vb  
' No call to Attach is necessary for inserts.  
Public Sub InsertOrder(ByVal o As Order)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    db.Orders.InsertOnSubmit(o)  
  
    ' Exception handling not shown.  
    db.SubmitChanges()  
  
End Sub  
```  
  
```csharp  
// No call to Attach is necessary for inserts.  
    public void InsertOrder(Order o)  
    {  
        NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
        db.Orders.InsertOnSubmit(o);  
  
        // Exception handling not shown.  
        db.SubmitChanges();  
    }  
```  
  
## <a name="deleting-data"></a><span data-ttu-id="c0252-144">删除数据</span><span class="sxs-lookup"><span data-stu-id="c0252-144">Deleting Data</span></span>  

 <span data-ttu-id="c0252-145">为了从数据库删除现有对象，表示层调用中间层接口上的相关方法，并传入要删除的对象的副本（其中包含该对象的原始值）。</span><span class="sxs-lookup"><span data-stu-id="c0252-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="c0252-146">删除操作涉及到开放式并发检查，并且必须首先将要删除的对象附加到新的数据上下文。</span><span class="sxs-lookup"><span data-stu-id="c0252-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="c0252-147">在此示例中，`Boolean` 参数设置为 `false`，以指示该对象没有时间戳 (RowVersion)。</span><span class="sxs-lookup"><span data-stu-id="c0252-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="c0252-148">如果数据库表确实为每个记录生成了时间戳，则并发检查会简单得多（特别是对客户端而言）。</span><span class="sxs-lookup"><span data-stu-id="c0252-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="c0252-149">只需传入原始对象或已修改的对象，并将 `Boolean` 参数设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="c0252-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="c0252-150">在任何情况下，通常都需要在中间层上捕捉 <xref:System.Data.Linq.ChangeConflictException>。</span><span class="sxs-lookup"><span data-stu-id="c0252-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="c0252-151">有关如何处理开放式并发冲突的详细信息，请参阅 [乐观 concurrency：概述](optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c0252-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="c0252-152">如果要删除的实体具有对关联表的外键约束，则必须首先删除该实体的 <xref:System.Data.Linq.EntitySet%601> 集合中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="c0252-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
```vb  
' Attach is necessary for deletes.  
Public Sub DeleteOrder(ByVal order As Order)  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
  
    db.Orders.Attach(order, False)  
    ' This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order)  
  
    Try  
        ' ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict)  
  
    Catch ex As ChangeConflictException  
        ' Get conflict information, and take actions  
        ' that are appropriate for your application.  
        ' See MSDN Article "How to: Manage Change  
        ' Conflicts (LINQ to SQL).  
  
    End Try  
End Sub  
```  
  
```csharp  
// Attach is necessary for deletes.  
public void DeleteOrder(Order order)  
{  
    NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
  
    db.Orders.Attach(order, false);  
    // This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order);  
    try  
    {  
        // ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict);  
    }  
    catch (ChangeConflictException e)  
    {  
       // Get conflict information, and take actions  
       // that are appropriate for your application.  
       // See MSDN Article How to: Manage Change Conflicts (LINQ to SQL).  
    }  
}  
```  
  
## <a name="updating-data"></a><span data-ttu-id="c0252-153">更新数据</span><span class="sxs-lookup"><span data-stu-id="c0252-153">Updating Data</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c0252-154">支持以下这些涉及开放式并发的方案中的更新：</span><span class="sxs-lookup"><span data-stu-id="c0252-154">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
- <span data-ttu-id="c0252-155">基于时间戳或 RowVersion 号的开放式并发。</span><span class="sxs-lookup"><span data-stu-id="c0252-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
- <span data-ttu-id="c0252-156">基于实体属性子集的原始值的开放式并发。</span><span class="sxs-lookup"><span data-stu-id="c0252-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
- <span data-ttu-id="c0252-157">基于完整原始实体和已修改实体的开放式并发。</span><span class="sxs-lookup"><span data-stu-id="c0252-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="c0252-158">还可以对实体及其关系（如一个 Customer 及其关联 Order 对象的集合）一起执行更新或删除。</span><span class="sxs-lookup"><span data-stu-id="c0252-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="c0252-159">如果在客户端上对实体对象及其子代 (`EntitySet`) 集合的关系图进行修改，并且开放式并发检查需要原始值，则客户端必须为每个实体和 <xref:System.Data.Linq.EntitySet%601> 对象提供这些原始值。</span><span class="sxs-lookup"><span data-stu-id="c0252-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="c0252-160">如果需要使客户端可以在单个方法调用中进行一组相关的更新、删除和插入操作，则必须为客户端提供一种相应的方式，以便指示要对每个实体执行的操作的类型。</span><span class="sxs-lookup"><span data-stu-id="c0252-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="c0252-161">然后，在调用 <xref:System.Data.Linq.ITable.Attach%2A> 之前，必须在中间层上为每个实体调用适当的 <xref:System.Data.Linq.ITable.InsertOnSubmit%2A> 方法，然后依次调用 <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>、<xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> 或 `Attach`（对于插入操作，不调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>）。</span><span class="sxs-lookup"><span data-stu-id="c0252-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="c0252-162">在尝试进行更新之前，不要将从数据库中检索数据作为一种获取原始值的方式。</span><span class="sxs-lookup"><span data-stu-id="c0252-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="c0252-163">有关开放式并发的详细信息，请参阅 [乐观 concurrency：概述](optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c0252-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="c0252-164">有关解决开放式并发更改冲突的详细信息，请参阅 [如何：管理更改冲突](how-to-manage-change-conflicts.md)。</span><span class="sxs-lookup"><span data-stu-id="c0252-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="c0252-165">下面的示例演示每种方案：</span><span class="sxs-lookup"><span data-stu-id="c0252-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="c0252-166">使用时间戳的开放式并发</span><span class="sxs-lookup"><span data-stu-id="c0252-166">Optimistic concurrency with timestamps</span></span>  
  
```vb  
' Assume that "customer" has been sent by client.  
' Attach with "true" to say this is a modified entity  
' and it can be checked for optimistic concurrency  
' because it has a column that is marked with the  
' "RowVersion" attribute.  
  
db.Customers.Attach(customer, True)  
  
Try  
    ' Optional: Specify a ConflictMode value  
    ' in call to SubmitChanges.  
    db.SubmitChanges()  
Catch ex As ChangeConflictException  
    ' Handle conflict based on options provided.  
    ' See MSDN article "How to: Manage Change  
    ' Conflicts (LINQ to SQL)".  
End Try  
```  
  
```csharp  
// Assume that "customer" has been sent by client.  
// Attach with "true" to say this is a modified entity  
// and it can be checked for optimistic concurrency because  
//  it has a column that is marked with "RowVersion" attribute  
db.Customers.Attach(customer, true)  
try  
{  
    // Optional: Specify a ConflictMode value  
    // in call to SubmitChanges.  
    db.SubmitChanges();  
}  
catch(ChangeConflictException e)  
{  
    // Handle conflict based on options provided  
    // See MSDN article How to: Manage Change Conflicts (LINQ to SQL).  
}  
```  
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="c0252-167">使用原始值子集的开放式并发</span><span class="sxs-lookup"><span data-stu-id="c0252-167">With Subset of Original Values</span></span>  

 <span data-ttu-id="c0252-168">在此方法中，客户端返回完整的序列化对象以及要修改的值。</span><span class="sxs-lookup"><span data-stu-id="c0252-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
```vb  
Public Sub UpdateProductInventory(ByVal p As Product, ByVal _  
    unitsInStock As Short?, ByVal unitsOnOrder As Short?)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        ' p is the original unmodified product  
        ' that was obtained from the database.  
        ' The client kept a copy and returns it now.  
        db.Products.Attach(p, False)  
  
        ' Now that the original values are in the data context,  
        ' apply the changes.  
        p.UnitsInStock = unitsInStock  
        p.UnitsOnOrder = unitsOnOrder  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle conflict based on options provided.  
            ' See MSDN article "How to: Manage Change Conflicts  
            ' (LINQ to SQL)".  
        End Try  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInventory(Product p, short? unitsInStock, short? unitsOnOrder)  
{  
    using (NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString))  
    {  
        // p is the original unmodified product  
        // that was obtained from the database.  
        // The client kept a copy and returns it now.  
        db.Products.Attach(p, false);  
  
        // Now that the original values are in the data context, apply the changes.  
        p.UnitsInStock = unitsInStock;  
        p.UnitsOnOrder = unitsOnOrder;  
        try  
        {  
             // Optional: Specify a ConflictMode value  
             // in call to SubmitChanges.  
             db.SubmitChanges();  
        }  
        catch (ChangeConflictException e)  
        {  
            // Handle conflict based on provided options.  
            // See MSDN article How to: Manage Change Conflicts  
            // (LINQ to SQL).  
        }  
    }  
}  
```  
  
### <a name="with-complete-entities"></a><span data-ttu-id="c0252-169">使用完整实体的开放式并发</span><span class="sxs-lookup"><span data-stu-id="c0252-169">With Complete Entities</span></span>  
  
```vb  
Public Sub UpdateProductInfo(ByVal newProd As Product, ByVal _  
    originalProd As Product)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        db.Products.Attach(newProd, originalProd)  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle potential change conflicgt in whatever way  
            ' is appropriate for your application.  
            ' For more information, see the MSDN article  
            ' "How to: Manage Change Conflicts (LINQ to  
            ' SQL)".  
        End Try  
  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInfo(Product newProd, Product originalProd)  
{  
     using (NorthwindClasses1DataContext db = new  
        NorthwindClasses1DataContext(connectionString))  
     {  
         db.Products.Attach(newProd, originalProd);  
         try  
         {  
               // Optional: Specify a ConflictMode value  
               // in call to SubmitChanges.  
               db.SubmitChanges();  
         }  
        catch (ChangeConflictException e)  
        {  
            // Handle potential change conflict in whatever way  
            // is appropriate for your application.  
            // For more information, see the MSDN article  
            // How to: Manage Change Conflicts (LINQ to SQL)/  
        }
    }  
}  
```  
  
 <span data-ttu-id="c0252-170">若要更新集合，请调用 <xref:System.Data.Linq.ITable.AttachAll%2A> 而不是 `Attach`。</span><span class="sxs-lookup"><span data-stu-id="c0252-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="c0252-171">期望的实体成员</span><span class="sxs-lookup"><span data-stu-id="c0252-171">Expected Entity Members</span></span>  

 <span data-ttu-id="c0252-172">如前所述，在调用 `Attach` 方法之前，只需设置实体对象的特定成员。</span><span class="sxs-lookup"><span data-stu-id="c0252-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="c0252-173">需要设置的实体成员必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="c0252-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
- <span data-ttu-id="c0252-174">属于实体的标识。</span><span class="sxs-lookup"><span data-stu-id="c0252-174">Be part of the entity’s identity.</span></span>  
  
- <span data-ttu-id="c0252-175">需要进行修改。</span><span class="sxs-lookup"><span data-stu-id="c0252-175">Be expected to be modified.</span></span>  
  
- <span data-ttu-id="c0252-176">为时间戳，或将其 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 属性设置为除 `Never` 之外的某个值。</span><span class="sxs-lookup"><span data-stu-id="c0252-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="c0252-177">如果某个表使用时间戳或版本号进行开放式并发检查，则在调用 <xref:System.Data.Linq.ITable.Attach%2A> 之前必须设置这些成员。</span><span class="sxs-lookup"><span data-stu-id="c0252-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="c0252-178">当该 Column 属性 (Attribute) 上的 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 属性 (Property) 设置为 true 时，相应的成员将专门用于进行开放式并发检查。</span><span class="sxs-lookup"><span data-stu-id="c0252-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="c0252-179">只有当数据库具有相同的版本号或时间戳值时，才会提交所请求的任何更新。</span><span class="sxs-lookup"><span data-stu-id="c0252-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="c0252-180">只要成员的 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 未设置为 `Never`，那么也会在开放式并发检查中使用该成员。</span><span class="sxs-lookup"><span data-stu-id="c0252-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="c0252-181">如果未指定其他值，则默认值为 `Always`。</span><span class="sxs-lookup"><span data-stu-id="c0252-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="c0252-182">如果缺少这些必需成员中的任何一个成员，都会在 <xref:System.Data.Linq.ChangeConflictException> 期间引发 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>（“找不到行或行已更改”）。</span><span class="sxs-lookup"><span data-stu-id="c0252-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="c0252-183">状态</span><span class="sxs-lookup"><span data-stu-id="c0252-183">State</span></span>  

 <span data-ttu-id="c0252-184">在将一个实体对象附加到 <xref:System.Data.Linq.DataContext> 实例之后，会将该对象视为处于 `PossiblyModified` 状态。</span><span class="sxs-lookup"><span data-stu-id="c0252-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="c0252-185">可通过三种方式强制所附加的对象被视为 `Modified`。</span><span class="sxs-lookup"><span data-stu-id="c0252-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="c0252-186">将对象作为未修改的对象进行附加，然后直接修改其字段。</span><span class="sxs-lookup"><span data-stu-id="c0252-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="c0252-187">使用接受当前对象实例和原始对象实例作为参数的 <xref:System.Data.Linq.Table%601.Attach%2A> 重载附加对象。</span><span class="sxs-lookup"><span data-stu-id="c0252-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="c0252-188">这会向更改跟踪程序提供旧值和新值，以便跟踪程序自动了解哪些字段已更改。</span><span class="sxs-lookup"><span data-stu-id="c0252-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="c0252-189">使用接受另一个布尔型参数（设置为 true）的 <xref:System.Data.Linq.Table%601.Attach%2A> 重载附加对象。</span><span class="sxs-lookup"><span data-stu-id="c0252-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="c0252-190">这将告诉更改跟踪程序将该对象视为已修改的对象，而无需提供任何原始值。</span><span class="sxs-lookup"><span data-stu-id="c0252-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="c0252-191">在此方式中，对象必须具有一个版本/时间戳字段。</span><span class="sxs-lookup"><span data-stu-id="c0252-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="c0252-192">有关详细信息，请参阅 [对象状态和更改跟踪](object-states-and-change-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="c0252-192">For more information, see [Object States and Change-Tracking](object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="c0252-193">如果 ID 缓存中已存在一个实体对象且该对象具有与要附加的对象相同的标识，则会引发 <xref:System.Data.Linq.DuplicateKeyException>。</span><span class="sxs-lookup"><span data-stu-id="c0252-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="c0252-194">在附加一组 `IEnumerable` 对象时，将在出现已存在的键时引发 <xref:System.Data.Linq.DuplicateKeyException>。</span><span class="sxs-lookup"><span data-stu-id="c0252-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="c0252-195">剩余的对象将不会附加。</span><span class="sxs-lookup"><span data-stu-id="c0252-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0252-196">请参阅</span><span class="sxs-lookup"><span data-stu-id="c0252-196">See also</span></span>

- [<span data-ttu-id="c0252-197">N 层和远程应用程序与 LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c0252-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="c0252-198">背景信息</span><span class="sxs-lookup"><span data-stu-id="c0252-198">Background Information</span></span>](background-information.md)
